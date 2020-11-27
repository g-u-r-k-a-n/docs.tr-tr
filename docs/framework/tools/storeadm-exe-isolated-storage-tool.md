---
title: Storeadm.exe (Yalıtılmış Depolama Aracı)
description: Yalıtılmış depolama aracı Storeadm.exe hakkında bilgi edinin. Bu araç, geçerli kullanıcı için varolan tüm depoları listeler veya kaldırır.
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
ms.openlocfilehash: 974f3c464ff686a486657d08e77c97299cc94732
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283841"
---
# <a name="storeadmexe-isolated-storage-tool"></a>Storeadm.exe (Yalıtılmış Depolama Aracı)

Yalıtılmış Depolama aracı, geçerli kullanıcı için varolan tüm depoları listeler veya kaldırır.  
  
 Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir. Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın. Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).  
  
 Komut satırına şunu yazın:  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a>Parametreler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/h**[**ELP**]|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|**/List**|Geçerli kullanıcı için varolan tüm depoları görüntüler. Buna, kullanıcı tarafından çalıştırılan tüm uygulamaların veya derlemelerin depoları dahildir.|  
|**/MACHINE**|Makine deposunu seçer. Eylemin Makine deposuna uygulanması gerektiğini belirtmek için bu seçeneği **/list** veya **/Remove** seçeneğiyle birlikte kullanın.<br /><br /> .NET Framework 2.0'da yeni bir özelliktir|  
|**/**|Sessiz mod kullanılacağını belirtir; yalnızca hata iletileri görünecek şekilde bilgilendirici çıktıyı engeller.|  
|**/Remove**|Geçerli kullanıcı için varolan tüm depoları kalıcı olarak kaldırır.|  
|**/dolaşım**|Dolaşım deposunu seçer. Eylemin dolaşım deposuna uygulanması gerektiğini belirtmek için bu seçeneği **/list** veya **/Remove** seçenekleriyle birlikte kullanın.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  

 Herhangi bir seçenek belirtmeden Storeadm.exe'yi komut satırından çalıştırmak sözdizimini ve araç için seçenekleri görüntüler.  
  
 **/List** ve **/Remove** seçenekleri genellikle tek seferde kullanılır; Ancak, iki veya daha fazla seçenek belirtilirse, komut satırında göründükleri sırada gerçekleştirilir.  
  
 Uygulamaların, bir kullanıcı için iki depodan birine veya makine deposuna kaydetme seçeneği vardır:  
  
- Kullanıcı için Kullanıcı veri dolaşımı etkin olsa bile yerel depo, dolaşımda olmayan (Windows 2000 ve üzeri) bir konumda bulunur.  
  
- Dolaşım deposu, dolaşımda bulunan bir konumda bulunur, ancak yalnızca Windows NT yönetimi aracılığıyla Kullanıcı için dolaşım etkinse bu işlemi yapabilirsiniz.  
  
- Makine deposu bir makinedeki tüm kullanıcılar için ortaktır ve o makinede ortak bir dizin altında depolanır.  
  
    > [!NOTE]
    > Makine deposu .NET Framework sürüm 2.0'da yeni bir özelliktir.  
  
 Dolaşımın kullanıcı için etkinleştirilip etkinleştirilmediği Storeadm.exe'nin yönetimini etkilemez. Aracı hiçbir seçenek olmadan çalıştırmak yerel depoya tüm işlemleri uygular. Aracı **/dolaşım** seçeneğiyle çalıştırmak, tüm işlemleri dolaşımda olan depoya uygular. Aracı **/MACHINE** seçeneğiyle çalıştırmak, tüm eylemleri Makine deposuna uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Araçlar](index.md)
- [Yalıtılmış depolama](../../standard/io/isolated-storage.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)
