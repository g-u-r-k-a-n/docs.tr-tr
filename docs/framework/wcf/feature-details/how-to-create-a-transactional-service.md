---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Işlemsel hizmet oluşturma'
title: 'Nasıl yapılır: İşlemsel Hizmet Oluşturma'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: 78ad922a7e1f174715be7bd1a8466572425411be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643442"
---
# <a name="how-to-create-a-transactional-service"></a>Nasıl yapılır: İşlemsel Hizmet Oluşturma

Bu örnek, işlemsel bir hizmet oluşturmanın ve hizmet işlemlerini koordine etmek için istemci tarafından başlatılan bir işlemin kullanımını gösterir.  
  
### <a name="creating-a-transactional-service"></a>İşlemsel hizmet oluşturma  
  
1. Gelen işlem gereksinimlerini belirtmek için, bir hizmet sözleşmesi oluşturun ve istenen ayarı <xref:System.ServiceModel.TransactionFlowOption> Numaralandırmadaki işlemlere ekleyin. Ayrıca, uygulanan hizmet sınıfına da yerleştirebileceğinizi unutmayın <xref:System.ServiceModel.TransactionFlowAttribute> . Bu, bir arabirimin tek bir uygulamasının her uygulama yerine bu işlem ayarlarını kullanmasına olanak sağlar.  
  
    ```csharp
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2. Bir uygulama sınıfı oluşturun ve <xref:System.ServiceModel.ServiceBehaviorAttribute> isteğe bağlı olarak bir ve belirtmek için öğesini kullanın <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> . Çoğu durumda, varsayılan değer olan <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 60 saniye ve varsayılan değer olarak uygun olduğunu unutmayın <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> `Unspecified` . Her işlem için, <xref:System.ServiceModel.OperationBehaviorAttribute> yöntemi içinde gerçekleştirilen çalışmanın, özniteliğin değerine göre bir işlem kapsamı kapsamında gerçekleşmeyeceğini belirtmek için özniteliğini kullanabilirsiniz <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> . Bu durumda, yöntemi için kullanılan işlem, `Add` istemciden aktarılan zorunlu gelen işlemle aynıdır ve yöntemi için kullanılan işlem `Subtract` , istemciden veya yeni bir örtük olarak oluşturulan yeni bir işlem olduğunda gelen işlem ile aynıdır.  
  
    ```csharp
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n1} to {n2}");
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n2} from {n1}");
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3. Yapılandırma dosyasında, işlem bağlamının akışını ve bunu yapmak için kullanılacak protokolleri belirten bağlamaları yapılandırın. Daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](servicemodel-transaction-configuration.md). Özellikle, bağlama türü, uç nokta öğesinin `binding` özniteliğinde belirtilir. [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md)Öğesi `bindingConfiguration` `transactionalOleTransactionsTcpBinding` , aşağıdaki örnek yapılandırmada gösterildiği gibi adlı bir bağlama yapılandırmasına başvuran bir özniteliği içerir.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     İşlem akışı, özniteliği kullanılarak yapılandırma düzeyinde etkinleştirilir `transactionFlow` ve işlem protokolü `transactionProtocol` Aşağıdaki yapılandırmada gösterildiği gibi özniteliği kullanılarak belirtilir.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Birden çok işlem protokolünü destekleme  
  
1. En iyi performans için, Windows Communication Foundation (WCF) kullanılarak yazılmış bir istemciyi ve hizmeti içeren senaryolar için OleTransactions protokolünü kullanmanız gerekir. Ancak, WS-AtomicTransaction (WS-AT) protokolü, üçüncü taraf protokol yığınları ile birlikte çalışabilirlik gerektiğinde senaryolar için yararlıdır. Aşağıdaki örnek yapılandırmada gösterildiği gibi, uygun protokole özgü bağlamaları olan birden fazla uç nokta sağlayarak WCF hizmetlerini her iki protokolü de kabul edecek şekilde yapılandırabilirsiniz.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     İşlem protokolü özniteliği kullanılarak belirtilir `transactionProtocol` . Ancak, bu öznitelik `wsHttpBinding` yalnızca ws-at protokolünü kullanabilmesi için, bu öznitelik sistem tarafından sağlanmamıştır.  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a>Bir işlemin tamamlanmasını denetleme  
  
1. Varsayılan olarak, işlenmeyen özel durum oluşturulmaz, WCF işlemleri işlemleri otomatik olarak tamamlar. Bu davranışı <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> özelliğini ve yöntemini kullanarak değiştirebilirsiniz <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> . Bir işlemin başka bir işlemle aynı işlem içinde gerçekleşmesi gerektiğinde (örneğin, bir borç ve kredi işlemi), <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> `false` aşağıdaki işlem örneğinde gösterildiği gibi özelliğini olarak ayarlayarak otomatik tamamlama davranışını devre dışı bırakabilirsiniz `Debit` . İşlemin kullandığı işlem, işlem içinde `Debit` gösterildiği gibi, özelliği olarak ayarlanmış bir yöntem çağrılana kadar ya da işlem, işlemde <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> `true` `Credit1` <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> gösterildiği gibi işlemi tamamlandı olarak işaretlemek üzere çağrıldığında `Credit2` işlem tamamlanmaz. İki kredi işleminin illüstrasyon amacıyla gösterildiğini ve tek bir kredi işleminin daha tipik olduğunu unutmayın.  
  
    ```csharp
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2. İşlem bağıntı amaçları doğrultusunda, özelliği olarak ayarlamak, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> `false` bir oturumsuz bağlamanın kullanılmasını gerektirir. Bu gereksinim `SessionMode` , üzerinde özelliği ile belirtilir <xref:System.ServiceModel.ServiceContractAttribute> .  
  
    ```csharp
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Bir işlem hizmeti örneğinin ömrünü denetleme  
  
1. WCF, <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> bir işlem tamamlandığında temeldeki hizmet örneğinin serbest bırakılıp başlatılmayacağını belirtmek için özelliğini kullanır. Bu varsayılan olarak `true` , aksi belirtilmedikçe, WCF etkin ve öngörülebilir bir "tam zamanında" etkinleştirme davranışı sergiler. Sonraki bir işlem üzerindeki bir hizmete yapılan çağrılar, önceki işlemin durumuna göre hiçbir şekilde, yeni bir hizmet örneğini garanti altına alır. Bu genellikle yararlı olsa da, bazen işlem tamamlandıktan sonra hizmet örneği içinde durumu korumak isteyebilirsiniz. Bunun örnekleri, gerekli durum veya kaynak tanıtıcılarının alınması veya edilmeyen ne kadar pahalı olduğu durumdur. Bunu, <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> özelliğini olarak ayarlayarak yapabilirsiniz `false` . Bu ayar ile, örnek ve ilişkili herhangi bir durum sonraki çağrılarda kullanılabilir olacaktır. Bunu kullanırken, durum ve işlemlerin ne zaman ve nasıl temizleneceği ve tamamlanalınacağını göz önünde bulundurun. Aşağıdaki örnek, örneği değişkenle birlikte tutarak bunun nasıl yapılacağını gösterir `runningTotal` .  
  
    ```csharp
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n} to {runningTotal}");
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n} from {runningTotal}");
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    > Örnek yaşam süresi, hizmete iç bir davranış olduğundan ve özelliği aracılığıyla denetlendiğinden <xref:System.ServiceModel.ServiceBehaviorAttribute> , örnek davranışını ayarlamak için hizmet yapılandırmasında veya hizmet sözleşmesinde hiçbir değişiklik yapılması gerekmez. Ayrıca, hat bunun gösterimini içermez.
