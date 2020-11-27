---
title: İş Akışı Denetim Uç Noktası
ms.date: 03/30/2017
ms.assetid: 1b883334-1590-4fbb-b0d6-65197efe0700
ms.openlocfilehash: ecc0946833db578c524ce7e4579024bd4cd46fd0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266902"
---
# <a name="workflow-control-endpoint"></a>İş Akışı Denetim Uç Noktası

İş akışı denetim uç noktası, geliştiricilerin kullanılarak barındırılan iş akışı örneklerini uzaktan denetlemek için denetim işlemlerini çağırmasını sağlar <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Bu özellik, askıya alma, geri alma ve sonlandırma gibi denetim işlemlerini programlı bir şekilde gerçekleştirmek için kullanılabilir.  
  
> [!WARNING]
> İş akışı denetim uç noktası bir işlem içinde kullanılıyorsa ve denetlenen iş akışı bir etkinlik içeriyorsa <xref:System.Activities.Statements.Persist> , iş akışı örneği işlem zaman aşımına uğrayana kadar engeller.  
  
## <a name="workflow-instance-management"></a>İş akışı örneği yönetimi  

 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] adlı yeni bir sözleşme tanımlar <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> . Bu sözleşme tarafından barındırılan iş akışı örneklerini uzaktan denetlemenize izin veren bir dizi denetim işlemi tanımlar <xref:System.ServiceModel.Activities.WorkflowServiceHost> . <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> , sözleşmenin bir uygulamasını sağlayan standart bir uç noktasıdır <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> . <xref:System.ServiceModel.Activities.WorkflowControlClient> , denetim işlemlerini öğesine göndermek için kullanılan bir sınıftır <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> .  
  
 İş akışı örnekleri aşağıdaki durumlardan birinde olabilir:  
  
 Etkin  
 Bir iş akışı örneğinin tamamlandı durumuna ulaşmadan önce ve askıya alınma durumunda olmayan durumu. Bu durumda iş akışı örneği, uygulama iletilerini çalıştırır ve işler.  
  
 Askıya alındı  
 Bu durumda, çalışmayı başlatmayan veya kısmen çalıştırılmış etkinlikler olsa bile iş akışı örneği çalışmaz.  
  
 Tamamlandı  
 Bir iş akışı örneğinin son durumu. İş akışı örneği, tamamlanan duruma ulaştıktan sonra çalıştırılamaz.  
  
## <a name="iworkflowinstancemanagement"></a>IWorkflowInstanceManagement  

 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>Arabirim, zaman uyumlu ve zaman uyumsuz sürümlerle denetim işlemleri kümesi tanımlar. İşlem temelli sürümler için işlem kullanan bir bağlamanın kullanılması gerekir. Aşağıdaki tabloda desteklenen denetim işlemleri listelenmektedir.  
  
|Denetim Işlemi|Açıklama|  
|-----------------------|-----------------|  
|Durdurma|İş akışı örneğinin yürütülmesini zorla durdur.|  
|İptal|Bir iş akışı örneğini etkin veya askıya alınmış durumdan tamamlandı durumuna geçirir.|  
|Çalıştır|Yürütme fırsatı için bir iş akışı örneği sağlar.|  
|Askıya Alma|Etkin durumdan askıya alınmış duruma bir iş akışı örneği geçirir.|  
|Terminate|Bir iş akışı örneğini etkin veya askıya alınmış durumdan tamamlandı durumuna geçirir.|  
|Erişimi iade etme|Bir iş akışı örneğini askıya alınan durumdan etkin duruma geçirir.|  
|TransactedCancel|Bir işlem altında (istemciden akışlı veya yerel olarak oluşturulan) Iptal işlemini gerçekleştirir. Sistem iş akışı örneğinin dayanıklı durumunu koruyorsa, bu işlemin yürütülmesi sırasında iş akışı örneği kalıcı olmalıdır.|  
|TransactedRun|Çalıştırma işlemini bir işlem altında gerçekleştirir (istemciden veya yerel olarak oluşturulur). Sistem iş akışı örneğinin dayanıklı durumunu koruyorsa, bu işlemin yürütülmesi sırasında iş akışı örneği kalıcı olmalıdır.|  
|TransactedSuspend|Askıya alma işlemini bir işlem altında gerçekleştirir (istemciden veya yerel olarak oluşturulur). Sistem iş akışı örneğinin dayanıklı durumunu koruyorsa, bu işlemin yürütülmesi sırasında iş akışı örneği kalıcı olmalıdır.|  
|TransactedTerminate|Sonlandırma işlemini bir işlem altında gerçekleştirir (istemciden veya yerel olarak oluşturulur). Sistem iş akışı örneğinin dayanıklı durumunu koruyorsa, bu işlemin yürütülmesi sırasında iş akışı örneği kalıcı olmalıdır.|  
|TransactedUnsuspend|Bir işlem altında (istemciden akışlı veya yerel olarak oluşturulan) askıya alma işlemini gerçekleştirir. Sistem iş akışı örneğinin dayanıklı durumunu koruyorsa, bu işlemin yürütülmesi sırasında iş akışı örneği kalıcı olmalıdır.|  
  
 <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement>Sözleşme, yalnızca mevcut iş akışı örneklerini yönetmek için yeni bir iş akışı örneği oluşturmak için bir yol sağlamaz. Yeni bir iş akışı örneğinin uzaktan oluşturulması hakkında daha fazla bilgi için bkz. [Iş akışı hizmeti konak genişletilebilirliği](workflow-service-host-extensibility.md).  
  
## <a name="workflowcontrolendpoint"></a>WorkflowControlEndpoint  

 <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> , sabit bir sözleşmeye sahip standart bir uç noktasıdır <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> . Bir <xref:System.ServiceModel.Activities.WorkflowServiceHost> örneğe eklendiğinde, bu uç nokta daha sonra ana bilgisayar örneği tarafından barındırılan herhangi bir iş akışı örneğine komut işlemlerini göndermek için kullanılabilir. Standart uç noktalar hakkında daha fazla bilgi için bkz. [standart uç noktalar](standard-endpoints.md).  
  
## <a name="workflowcontrolclient"></a>WorkflowControlClient  

 <xref:System.ServiceModel.Activities.WorkflowControlClient> , bir üzerinde öğesine denetim iletileri göndermenizi sağlayan bir sınıftır <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Bu, anlaşma tarafından desteklenen işlemlerin her biri için, <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> işlem temelli işlemler haricinde bir yöntem içerir. <xref:System.ServiceModel.Activities.WorkflowControlClient> işlem temelli bir işlemin kullanılması gerekip gerekmediğini öğrenmek için çevresel işlemi kullanır.
