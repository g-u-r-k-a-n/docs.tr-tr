---
title: 'Nasıl yapılır: Özel İlke Onaylamalarını İçeri Aktarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: fb5e3ba5faca1b32eef63ac174bcd7731ee50771
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249156"
---
# <a name="how-to-import-custom-policy-assertions"></a>Nasıl yapılır: Özel İlke Onaylamalarını İçeri Aktarma

İlke onayları bir hizmet uç noktasının yeteneklerini ve gereksinimlerini anlatmaktadır.  İstemci uygulamaları, hizmet meta verilerinde ilke onayları kullanarak istemci bağlamasını yapılandırabilir veya bir hizmet uç noktası için hizmet sözleşmesini özelleştirebilir.  
  
 Özel ilke onayları, arabirimini uygulayarak içeri aktarılır <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> ve bu nesne meta veri sistemine geçirerek ya da uygulama yapılandırma dosyanıza uygulama türünü kaydederek içeri aktarılır.  <xref:System.ServiceModel.Description.IPolicyImportExtension>Arabirim uygulamalarının parametresiz bir Oluşturucu sağlaması gerekir.  
  
### <a name="to-import-custom-policy-assertions"></a>Özel ilke onaylamalarını içeri aktarmak için  
  
1. <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType>Arabirimini bir sınıfa uygulayın. Aşağıdaki yordamlara bakın.  
  
2. Özel ilke içe aktarıcı şu şekilde ekleyin:  
  
3. Yapılandırma dosyası kullanma. Aşağıdaki yordamlara bakın.  
  
4. [ServiceModel meta veri yardımcı programı aracıyla](../servicemodel-metadata-utility-tool-svcutil-exe.md)bir yapılandırma dosyası kullanma (Svcutil.exe). Aşağıdaki yordamlara bakın.  
  
5. İlke İçeri Aktarıcı programlı bir şekilde ekleniyor. Aşağıdaki yordamlara bakın.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Herhangi bir sınıfta System. ServiceModel. Description. IPolicyImportExtension arabirimini uygulamak için  
  
1. <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>Yönteminde, ilgilendiğiniz her ilke konusu için, yöntemine geçirilen nesne üzerinde uygun yöntemi (istediğiniz onaylama kapsamına bağlı olarak) çağırarak içeri aktarmak istediğiniz ilke onaylamalarını bulun <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> . Aşağıdaki kod örneği, <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> özel ilke onayını bulmak ve tek bir adımda koleksiyondan kaldırmak için yönteminin nasıl kullanılacağını gösterir. Onaylama işlemini bulmak ve kaldırmak için Remove yöntemini kullanırsanız, 4. adımı gerçekleştirmeniz gerekmez.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. İlke onaylamalarını işleyin. İlke sisteminin iç içe geçmiş ilkeleri ve ile normalleştirmediğini unutmayın `wsp:optional` . Bu yapıları ilke içeri aktarma uzantı uygulamanızda işlemelidir.  
  
3. İlke onaylama işlemi tarafından belirtilen yeteneği veya gereksinimi destekleyen bağlama veya sözleşmede özelleştirmeyi gerçekleştirin. Genellikle Onaylamalar, bir bağlamanın belirli bir yapılandırma veya belirli bir bağlama öğesi gerektirdiğini gösterir. Bu değişiklikleri özelliğe erişerek yapın <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType> . Diğer Onaylamalar, sözleşmeyi değiştirmenizi gerektirir.  Özelliği kullanarak sözleşmeye erişebilir ve bunları değiştirebilirsiniz <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType> .  İlke içeri aktarmalarınızın aynı bağlama ve anlaşma için birden çok kez çağrılabilecek olduğunu, ancak bir ilkeyi içeri aktarma işlemi başarısız olursa farklı ilke alternatiflerine sahip olabileceğini unutmayın. Kodunuzun bu davranışa dayanıklı olması gerekir.  
  
4. Özel ilke onayını onaylama koleksiyonundan kaldırın. Onaylama kaldırma Windows Communication Foundation (WCF), ilke içeri aktarmanın başarısız olduğunu varsayar ve ilişkili bağlamayı içeri aktarmaz. <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType>Özel ilke onaylama işlemini bulmak ve tek bir adımda koleksiyondan kaldırmak için yöntemini kullandıysanız, bu adımı gerçekleştirmeniz gerekmez.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Özel ilke alma aracını bir yapılandırma dosyası kullanarak meta veri sistemine eklemek için  
  
1. İçeri aktarma türünü, `<extensions>` [\<policyImporters>](../../configure-apps/file-schema/wcf/policyimporters.md) istemci yapılandırma dosyasındaki öğesinin içindeki öğesine ekleyin.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]
  
2. İstemci uygulamasında, <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> meta verileri çözümlemek için veya kullanın ve içeri aktarma otomatik olarak çağrılır.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Özel ilke içe aktarıcı Svcutil.exe kullanarak meta veri sistemine eklemek için  
  
1. İçeri aktarma türünü `<extensions>` [\<policyImporters>](../../configure-apps/file-schema/wcf/policyimporters.md) Svcutil.exe.config yapılandırma dosyasındaki öğesinin içindeki öğesine ekleyin. Ayrıca, seçeneği kullanılarak farklı bir yapılandırma dosyasına kayıtlı ilke İçeri Aktarıcı türlerini yüklemek için Svcutil.exe ' ı işaret edebilirsiniz `/svcutilConfig` .  
  
2. Meta verileri içeri aktarmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın ve içeri aktarma otomatik olarak çağrılır.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Özel ilke içe aktarıcı 'nın meta veri sistemine programlı bir şekilde eklenmesini sağlamak için  
  
1. <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType>Meta verileri içeri aktarmadan önce özelliğine içeri aktarma özelliğini ekleyin (örneğin, kullanıyorsanız <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> ).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Meta Veri Sistemini Genişletme](extending-the-metadata-system.md)
