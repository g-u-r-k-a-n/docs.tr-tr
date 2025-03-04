---
title: WCF'de Kimlik Doğrulama
description: WCF 'de, Windows kimlik doğrulaması, X. 509.440 sertifikaları ve Kullanıcı adı ve parola gibi kimlik doğrulaması sağlayan çeşitli mekanizmalar hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: e2334a8c024238f38e1c927a278a4e25e7dabd9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247544"
---
# <a name="authentication-in-wcf"></a>WCF'de Kimlik Doğrulama

Aşağıdaki konularda, kimlik doğrulaması (örneğin, Windows kimlik doğrulaması, X. 509.440 sertifikaları ve Kullanıcı adı ve parolalar) sağlayan Windows Communication Foundation (WCF) içinde çeşitli mekanizmalar gösterilmektedir.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Nasıl yapılır: ASP.NET Üyelik Sağlayıcısını Kullanma](how-to-use-the-aspnet-membership-provider.md)  
 ASP.NET özellikleri bir üyelik ve rol sağlayıcısı, kimlik doğrulaması için Kullanıcı adı/parola çiftlerini depolamak üzere bir veritabanı ve yetkilendirme için Kullanıcı rolleri içerir. Bu konuda, WCF hizmetlerinin, kullanıcıların kimliğini doğrulamak ve yetkilendirmek için aynı veritabanını nasıl kullanabileceği açıklanmaktadır.  
  
 [Nasıl yapılır: Özel Bir Kullanıcı Adı ve Parola Doğrulayıcı Kullanma](how-to-use-a-custom-user-name-and-password-validator.md)  
 Özel bir Kullanıcı adı/parola doğrulayıcının nasıl tümleştirileceğini gösterir.  
  
 [Kimlik Doğrulama ile Hizmet Kimliği](service-identity-and-authentication.md)  
 Bir istemci, ek bir güvenlik önlemi olarak hizmetin beklenen *kimliğini* belirterek hizmetin kimliğini doğrulayabilir. Beklenen kimlik ve hizmet tarafından döndürülen kimlik eşleşmiyorsa, kimlik doğrulaması başarısız olur.  
  
 [Güvenlik Görüşmeleri ve Zaman Aşımları](security-negotiation-and-timeouts.md)  
 Sınıfında özelliğinin nasıl kullanılacağını açıklar <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> .  
  
 [Windows Kimlik Doğrulama Hatalarını Ayıklama](debugging-windows-authentication-errors.md)  
 Windows kimlik doğrulaması kullanılırken karşılaşılan yaygın sorunlara odaklanır.  
  
## <a name="reference"></a>Başvuru  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Ortak Güvenlik Senaryoları](common-security-scenarios.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe genel bakış](security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))
