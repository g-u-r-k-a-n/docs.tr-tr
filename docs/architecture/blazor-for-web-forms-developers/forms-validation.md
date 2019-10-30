---
title: Formlar ve doğrulama
description: Blazor içinde istemci tarafı doğrulama ile form oluşturmayı öğrenin.
author: danroth27
ms.author: daroth
ms.date: 09/19/2019
ms.openlocfilehash: c30db5e06d36a6d15301835fe782b21058a80592
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088082"
---
# <a name="forms-and-validation"></a>Formlar ve doğrulama

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

ASP.NET Web Forms Framework, bir forma (`RequiredFieldValidator`, `CompareValidator`, `RangeValidator`vb.) girilen kullanıcı girişini doğrulamayı işleyen bir doğrulama sunucusu denetimleri kümesi içerir. ASP.NET Web Forms Framework, model bağlamayı ve veri ek açıklamalarına (`[Required]`, `[StringLength]`, `[Range]`, vb.) göre modeli doğrulamayı da destekler. Doğrulama mantığı hem sunucuda hem de istemci üzerinde, kaldırma JavaScript tabanlı doğrulama kullanılarak zorlanabilir. `ValidationSummary` sunucusu denetimi, kullanıcıya doğrulama hatalarının özetini göstermek için kullanılır.

Blazor, hem istemci hem de sunucu arasında doğrulama mantığının paylaşımını destekler. ASP.NET birçok ortak sunucu doğrulamayla önceden oluşturulmuş JavaScript uygulamaları sağlar. Çoğu durumda, geliştirici uygulamaya özgü doğrulama mantığını tam olarak uygulamak için JavaScript yazmak zorunda kalır. Aynı model türleri, veri ek açıklamaları ve doğrulama mantığı hem sunucu hem de istemcide kullanılabilir.

Blazor, bir giriş bileşenleri kümesi sağlar. Giriş bileşenleri, alan verilerini bir modele bağlamayı ve form gönderildiğinde kullanıcı girişini doğrulamayı işler.

|Giriş bileşeni|İşlenmiş HTML öğesi    |
|---------------|-------------------------|
|`InputCheckbox`|`<input type="checkbox">`|
|`InputDate`    |`<input type="date">`    |
|`InputNumber`  |`<input type="number">`  |
|`InputSelect`  |`<select>`               |
|`InputText`    |`<input>`                |
|`InputTextArea`|`<textarea>`             |

`EditForm` bileşeni, bu giriş bileşenlerini sarmalayan ve doğrulama işlemini bir `EditContext`aracılığıyla düzenler. `EditForm`oluştururken, `Model` parametresini kullanarak hangi model örneğinin bağlanılacağını belirlersiniz. Doğrulama genellikle veri ek açıklamaları kullanılarak yapılır ve genişletilebilir. Veri ek açıklaması tabanlı doğrulamayı etkinleştirmek için, `DataAnnotationsValidator` bileşenini `EditForm`alt öğesi olarak ekleyin. `EditForm` bileşeni, geçerli (`OnValidSubmit`) ve geçersiz (`OnInvalidSubmit`) gönderimlerini işlemek için uygun bir olay sağlar. Ayrıca, doğrulamayı kendiniz tetiklemenizi ve işlemenizi sağlayan daha genel `OnSubmit` bir olay da vardır.

Doğrulama hatası özetini göstermek için `ValidationSummary` bileşenini kullanın. Belirli bir giriş alanı için doğrulama iletilerini göstermek için, uygun model üyesine işaret eden `For` parametresi için bir lambda ifadesi belirterek `ValidationMessage` bileşenini kullanın.

Aşağıdaki model türü, veri ek açıklamalarını kullanarak çeşitli doğrulama kuralları tanımlar:

```csharp
using System;
using System.ComponentModel.DataAnnotations;

public class Starship
{
    [Required]
    [StringLength(16,
        ErrorMessage = "Identifier too long (16 character limit).")]
    public string Identifier { get; set; }

    public string Description { get; set; }

    [Required]
    public string Classification { get; set; }

    [Range(1, 100000,
        ErrorMessage = "Accommodation invalid (1-100000).")]
    public int MaximumAccommodation { get; set; }

    [Required]
    [Range(typeof(bool), "true", "true",
        ErrorMessage = "This form disallows unapproved ships.")]
    public bool IsValidatedDesign { get; set; }

    [Required]
    public DateTime ProductionDate { get; set; }
}
```

Aşağıdaki bileşen `Starship` model türüne göre Blazor içinde bir form oluşturmayı göstermektedir:

```razor
<h1>New Ship Entry Form</h1>

<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <p>
        <label for="identifier">Identifier: </label>
        <InputText id="identifier" @bind-Value="starship.Identifier" />
        <ValidationMessage For="() => starship.Identifier" />
    </p>
    <p>
        <label for="description">Description (optional): </label>
        <InputTextArea id="description" @bind-Value="starship.Description" />
    </p>
    <p>
        <label for="classification">Primary Classification: </label>
        <InputSelect id="classification" @bind-Value="starship.Classification">
            <option value="">Select classification ...</option>
            <option value="Exploration">Exploration</option>
            <option value="Diplomacy">Diplomacy</option>
            <option value="Defense">Defense</option>
        </InputSelect>
        <ValidationMessage For="() => starship.Classification" />
    </p>
    <p>
        <label for="accommodation">Maximum Accommodation: </label>
        <InputNumber id="accommodation" @bind-Value="starship.MaximumAccommodation" />
        <ValidationMessage For="() => starship.MaximumAccommodation" />
    </p>
    <p>
        <label for="valid">Engineering Approval: </label>
        <InputCheckbox id="valid" @bind-Value="starship.IsValidatedDesign" />
        <ValidationMessage For="() => starship.IsValidatedDesign" />
    </p>
    <p>
        <label for="productionDate">Production Date: </label>
        <InputDate id="productionDate" @bind-Value="starship.ProductionDate" />
        <ValidationMessage For="() => starship.ProductionDate" />
    </p>

    <button type="submit">Submit</button>
</EditForm>

@code {
    private Starship starship = new Starship();

    private void HandleValidSubmit()
    {
        // Save the data
    }
}
```

Form gönderildikten sonra, model bağlantılı veriler veritabanı gibi herhangi bir veri deposuna kaydedilmez. Blazor WebAssembly uygulamasında, verilerin sunucuya gönderilmesi gerekir. Örneğin, bir HTTP POST isteği kullanma. Bir Blazor sunucu uygulamasında veriler zaten sunucuda bulunur, ancak kalıcı olması gerekir. Blazor uygulamalarında veri erişiminin yönetilmesi, [verilerle ilgilenme](data.md) konusunun konusudur.

## <a name="additional-resources"></a>Ek kaynaklar

Blazor uygulamalarında [Formlar ve doğrulama](/aspnet/core/blazor/forms-validation) hakkında daha fazla bilgi için bkz. Blazor belgeleri.

>[!div class="step-by-step"]
>[Önceki](state-management.md)
>[İleri](data.md)
