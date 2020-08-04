---
title: Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)
description: Yönetim türü kesin belirlenmiş sınıf oluşturucusunun Mgmtclassgen.exe anlayın. Bu araç, bir WMI sınıfı için hızlı bir şekilde önceden bağlantılı yönetilen sınıf oluşturmanıza olanak sağlar.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
ms.openlocfilehash: 89facd4369dad6168e46febd3e34d7f7c235faf0
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517301"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a>Mgmtclassgen.exe (Yönetim Türü Kesin Belirlenmiş Sınıf Oluşturucu)
Yönetim Kesin Belirlenmiş Sınıf Üreticisi aracı, belirtilen bir Windows Yönetim Araçları (WMI) sınıfı için erken bağlı yönetilen bir sınıfı hızlı bir şekilde üretmenize olanak tanır. Oluşturulan sınıf, WMI sınıfının bir örneğine erişmek için yazmanız gereken kodu basitleştirir.  
  
## <a name="syntax"></a>Syntax  
  
```console  
mgmtclassgen
WMIClass [options]
```  
  
|Bağımsız Değişken|Açıklama|  
|--------------|-----------------|  
|*WMIClass*|Kendisi için erken bağlı yönetilen bir sınıf oluşturulacak Windows Yönetim Araçları sınıfı.|  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/l**  *dili*|Erken bağlı yönetilen sınıfın oluşturulacağı dili belirtir. **CS** (C#; varsayılan), **vb** (Visual Basic), **mc** (C++) veya **js** (JScript) dilini bağımsız değişkeni olarak belirtebilirsiniz.|  
|**/m**  *makinesi*|WMI sınıfının bulunduğu, bağlanılacak bilgisayarı belirtir. Varsayılan, yerel bilgisayardır.|  
|**/n**  *yolu*|WMI sınıfını içeren WMI ad alanına giden yolu belirtir. Bu seçeneği belirtmezseniz, araç varsayılan **root\cimv2** ad alanında *WMIClass* için kod üretir.|  
|**/o**  *classnamespace*|Yönetilen kod sınıfının içinde üretileceği .NET ad alanını belirtir. Bu seçeneği belirtmezseniz, araç ad alanını WMI ad alanını ve şema önekini kullanarak üretir. Şema öneki, sınıf adının alt çizgi karakterinden önce gelen parçasıdır. Örneğin, **root\cimv2** ad alanındaki **Win32_OperatingSystem** sınıfı Için, araç sınıfı kök içinde oluşturur **. CIMV2. Win32**.|  
|**/p**  *FilePath*|Üretilen kodun içinde kaydedileceği dosyanın yolunu belirtir. Bu seçeneği belirtmezseniz, araç dosyayı geçerli dizinde oluşturur. *WMIClass* bağımsız değişkenini kullanarak sınıfının oluşturduğu sınıf ve dosyayı adlandırır. Sınıfın adı ve dosya, WMIClass adıyla aynıdır *.* *WMIClass* bir alt çizgi karakteri içeriyorsa, araç alt çizgi karakterini izleyen sınıf adının bölümünü kullanır. Örneğin, *WMIClass* adı **Win32_LogicalDisk**biçimindeyse, oluşturulan sınıf ve dosya "MantıksalDisk" olarak adlandırılır. Bir dosya zaten varsa, araç varolan dosyanın üzerine yazar.|  
|**/PW**  *parolası*|**/M** seçeneği tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak parolayı belirtir.|  
|**/u**  *Kullanıcı adı*|**/M** seçeneği tarafından belirtilen bir bilgisayarda oturum açarken kullanılacak kullanıcı adını belirtir.|  
|**/?**|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Mgmtclassgen.exe yöntemini kullanır <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> . Bu nedenle, C#, Visual Basic ve JScript'ten başka yönetilen dillerde kod üretmek için, herhangi bir özel kod sağlayıcısını kullanabilirsiniz.  
  
 Üretilen sınıfların, kendisi için üretildikleri şemaya bağlı olduklarını unutmayın. Arka plandaki şema değişirse, şemada yapılan değişiklikleri yansıtmasını isterseniz, sınıfı yeniden oluşturmanız gerekir.  
  
 Aşağıdaki tabloda, WMI Ortak Bilgi Modeli (CIM) türlerinin üretilmiş bir sınıftaki veri türleriyle nasıl eşleştiği gösterilmektedir:  
  
|CIM türü|Oluşturulan sınıf içinde veri türü|  
|--------------|--------------------------------------|  
|CIM_SINT8|**SByte**|  
|CIM_UINT8|**Bayt**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**UInt32**|  
|CIM_SINT64|**Tutulamaz**|  
|CIM_UINT64|**UInt64**|  
|CIM_REAL32|**Tek**|  
|CIM_REAL64|**Çift**|  
|CIM_BOOLEAN|**Boole**|  
|CIM_String|**Dize**|  
|CIM_DATETIME|**DateTime** veya **TimeSpan**|  
|CIM_REFERENCE|**ManagementPath**|  
|CIM_CHAR16|**Char**|  
|CIM_OBJECT|**ManagementBaseObject**|  
|CIM_IUNKNOWN|**Nesne**|  
|CIM_ARRAY|Yukarıda sözü edilen nesnelerin dizisi|  
  
 Bir WMI sınıfı oluşturduğunuzda, aşağıdaki davranışlara dikkat edin:  
  
- Standart bir genel özelliğin veya yöntemin, varolan bir özellikle veya yöntemle aynı ada sahip olması olanaklıdır. Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.  
  
- Oluşturulan bir sınıftaki bir özellik veya yöntemin adının hedef programlama dilinde bir anahtar sözcük olması olanaklıdır. Bu durumda, araç, adlandırma çakışmalarından kaçınmak için, oluşturulan sınıfta özellik veya yöntemin adını değiştirir.  
  
- WMI'da, niteleyiciler bir sınıfı, örneği, özelliği veya yöntemi tanımlamak için bilgi içeren değiştiricilerdir. WMI, oluşturulmuş bir sınıftaki bir özelliği tanımlamakta kullanılacak **Read**, **Write**ve **Key** gibi standart niteleyicileri kullanır. Örneğin, bir **okuma** niteleyicisi ile değiştirilen bir özellik yalnızca oluşturulan sınıfta bir özellik **Get** erişimcisi ile tanımlanır. **Okuma** niteleyicisi ile işaretlenen bir özelliğin Salt okunabilir olması amaçlandığından, bir **küme** erişimcisi tanımlı değildir.  
  
- Değerin yalnızca belirtilen izin verilen değerlere ayarlanabileceği göstermek için **Values** ve **ValueMaps** niteleyicilerine göre sayısal bir özellik değiştirilebilir. Bu **değerler** ve **ValueMaps** ile bir numaralandırma oluşturulur ve özellik sabit listesine eşlenir.  
  
- WMI, yalnızca bir örneği olabilecek bir sınıf tanımlamak için singleton terimini kullanır. Bu nedenle, tek bir sınıf için parametresiz Oluşturucu sınıfı sınıfının tek örneğine başlatacak.  
  
- Bir WMI sınıfının, nesne olan özellikleri olabilir. Bu tür WMI sınıfı için kesin olarak belirlenmiş bir sınıf oluşturduğunuzda, katıştırılmış nesne özelliklerinin türleri için kesin olarak belirlenmiş sınıflar oluşturmayı düşünmelisiniz. Bu, katıştırılmış nesnelere türü kesin belirlenmiş bir şekilde erişmenize olanak tanır. Üretilen kodun gömülü nesnenin türünü algılayamayacağını unutmayın. Bu durumda, sorunu size bildirmek için, üretilen kodda bir açıklama oluşturulur. Sonra, özelliği üretilen diğer sınıfa yazmak için, üretilen kodu değiştirebilirsiniz.  
  
- WMI'da, CIM_DATETIME veri türünün veri değeri belirli bir tarih ve saati veya bir zaman aralığını gösterebilir. Veri değeri bir tarih ve saati gösteriyorsa, oluşturulan sınıftaki veri türü **DateTime**olur. Veri değeri bir zaman aralığını gösterirse, oluşturulan sınıftaki veri türü **TimeSpan**olur.  
  
 Alternatif olarak, Visual Studio .NET içindeki Sunucu Gezgini Management uzantısını kullanarak kesin türü belirtilmiş bir sınıf oluşturabilirsiniz.  
  
 WMI hakkında daha fazla bilgi için Platform SDK 'Sı belgelerindeki **Windows Yönetim Araçları** konusuna bakın.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki komut, **root\cimv2** ad alanındaki **Win32_LogicalDisk** WMI sınıfı için C# kodunda yönetilen bir sınıf oluşturur. Araç, yönetilen sınıfı kök içindeki c:\Disk.cs konumundaki kaynak dosyasına yazar **. CIMV2. Win32** ad alanı.  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 Aşağıdaki kod örneği, oluşturulan bir sınıfın programsal olarak nasıl kullanılacağını göstermektedir. İlk olarak, sınıfın bir örneği numaralandırılır ve yol yazdırılır. Ardından, başlatılacak oluşturulan sınıfın bir örneği bir WMI örneğiyle oluşturulur. `Process`, **Win32_Process** için oluşturulur ve `LogicalDisk` **root\cimv2** ad alanındaki **Win32_LogicalDisk** için oluşturulan sınıftır.  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App
   Public Shared Sub Main()
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [Araçlar](index.md)
- [Komut Istemleri](developer-command-prompt-for-vs.md)
