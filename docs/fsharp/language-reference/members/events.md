---
title: Olaylar
description: Olay çağrılarını F# , GUI programlamasında önemli olan Kullanıcı eylemleriyle ilişkilendirmenizi nasıl sağlayacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: ad60aff318832ab3ba5e9f7c43928898e171cea8
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543631"
---
# <a name="events"></a>Olaylar

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürür.  Docs.microsoft.com API başvurusu tamamlanmadı.

Olaylar, işlev çağrılarını kullanıcı eylemleriyle ilişkilendirmenize olanak tanır ve GUI programlamada önemlidir. Olaylar, uygulamalarınız veya işletim sistemi tarafından da tetiklenebilir.

## <a name="handling-events"></a>Olayları İşleme

Windows Forms veya Windows Presentation Foundation (WPF) gibi bir GUI kitaplığı kullandığınızda, uygulamanızdaki kodun çoğu kitaplık tarafından önceden tanımlanan olaylara yanıt olarak çalıştırılır. Bu önceden tanımlı olaylar, formlar ve denetimler gibi GUI sınıflarının üyeleridir. Aşağıdaki kodda gösterildiği gibi, bir düğmeye tıklama gibi, ilgili belirli bir olaya (örneğin, `Form` sınıfının `Click` olayı) başvurarak ve `Add` yöntemini çağırarak, önceden var olan bir olaya özel davranış ekleyebilirsiniz. Bunu etkileşimli 'den F# çalıştırırsanız, `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`çağrısını atlayın.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

`Add` yönteminin türü `('a -> unit) -> unit`. Bu nedenle, olay işleyicisi yöntemi genellikle olay bağımsız değişkenlerini bir parametre alır ve `unit`döndürür. Önceki örnekte, olay işleyici lambda ifadesi olarak gösterilmiştir. Olay işleyicisi, aşağıdaki kod örneğinde olduğu gibi, bir işlev değeri de olabilir. Aşağıdaki kod örneğinde, olay türüne özgü bilgiler sağlayan olay işleyicisi parametrelerinin kullanımı gösterilmektedir. `MouseMove` bir olay için sistem, işaretçinin `X` ve `Y` konumunu içeren bir `System.Windows.Forms.MouseEventArgs` nesnesi geçirir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a>Özel Olaylar Oluşturma

F#olaylar, [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) arabirimini F# uygulayan [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) sınıfı tarafından temsil edilir. `IEvent`, `System.IObservable<'T>` ve [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a)olmak üzere iki diğer arabirimin işlevselliğini birleştiren bir arabirimdir. Bu nedenle, `Event`s, diğer dillerdeki temsilcilerin eşdeğer işlevlerine `IObservable`ek olarak, F# olayların olay filtrelemesini desteklediği ve olay işleyicileri olarak birinci sınıf işlevleri ve Lambda ifadelerini F# kullandığı anlamına gelir. Bu işlevsellik [olay modülünde](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7)verilmiştir.

Tüm diğer .NET Framework olayları gibi davranan bir sınıfta bir olay oluşturmak için, sınıf içinde bir `Event` alan olarak bir tanımlayan `let` bağlama sınıfına ekleyin. İstenen olay bağımsız değişkeni türünü tür bağımsız değişkeni olarak belirtebilir veya boş bırakarak derleyicinin uygun türü ortaya çıkarmasını sağlayabilirsiniz. Ayrıca, olay CLI olayı olarak sunan bir olay üyesi de tanımlamanız gerekir. Bu üye [Clienevent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) özniteliğine sahip olmalıdır. Bir özellik gibi bildirilmiştir ve bunun uygulanması, etkinliğin [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) özelliğine yapılan bir çağrıdır. Sınıfınızın kullanıcıları, bir işleyici eklemek için yayımlanan olayın `Add` yöntemini kullanabilir. `Add` yönteminin bağımsız değişkeni bir lambda ifadesi olabilir. Olayı yükseltmek için olayın `Trigger` özelliğini kullanabilir ve bağımsız değişkenleri işleyici işlevine geçirerek. Aşağıdaki kod örneği bunu gösterir. Bu örnekte, olay için gösterilen tür bağımsız değişkeni, lambda ifadesi için bağımsız değişkenleri temsil eden bir kayıt düzenidir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

Çıktı aşağıdaki gibidir:

```console
Event1 occurred! Object data: Hello World!
```

`Event` modülü tarafından sunulan ek işlevler burada gösterilmektedir. Aşağıdaki kod örneği, bir olay ve tetikleyici yöntemi oluşturmak için `Event.create` temel kullanımını gösterir, lambda ifadeleri biçiminde iki olay işleyicisi ekler ve ardından her iki lambda ifadesini yürütmek için olayı tetikler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

Önceki kodun çıktısı aşağıdaki gibidir.

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a>Olay Akışını İşleme

Event [. Add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) işlevini kullanarak bir olay için yalnızca bir olay işleyicisi eklemek yerine, olayların akışlarını yüksek düzeyde özelleştirilmiş yollarla işlemek için `Event` modülündeki işlevleri kullanabilirsiniz. Bunu yapmak için, bir dizi işlev çağırmalarda ilk değer olarak olay ile birlikte ilet kanalını (`|>`) ve `Event` modülü sonraki işlev çağrıları gibi işlevlerini kullanırsınız.

Aşağıdaki kod örneği, işleyicinin yalnızca belirli koşullarda çağrıldığı bir olayın nasıl ayarlanacağını gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

[Observable modülü](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) , observable nesnelerinde çalışan benzer işlevleri içerir. Gözlemlenebilir nesneler olaylara benzer, fakat yalnızca, kendilerine abone olunuyorsa olaylara etkin olarak abone olurlar.

## <a name="implementing-an-interface-event"></a>Bir Arabirim Olayı Uygulama

UI bileşenleri geliştirirken, genellikle varolan bir formdan veya denetimden devralan yeni bir form veya yeni bir denetim oluşturarak başlarsınız. Olaylar genellikle bir arabirimde tanımlanır ve bu o durumda, olayı gerçekleştirmek için arabirimi gerçekleştirmeniz gerekir. `System.ComponentModel.INotifyPropertyChanged` arabirimi tek bir `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` olayını tanımlar. Aşağıdaki kod, bu devralınan arabirimde tanımlanan olayın nasıl uygulanacağını göstermektedir:

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

Olayı oluşturucuda bağlamak isterseniz, aşağıdaki örnekte olduğu gibi, olay kancasının ek bir oluşturucuda `then` bloğunda olması gerektiğinden, kod biraz daha karmaşıktır.

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a>Ayrıca bkz.

- [Üyeler](index.md)
- [Olayları işleme ve oluşturma](../../../standard/events/index.md)
- [Lambda Ifadeleri: `fun` anahtar sözcüğü](../functions/lambda-expressions-the-fun-keyword.md)
- [Control. Event modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [Control. Event&#60;'t&#62; sınıfı](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [Control. Event&#60;' Delegate, ' args&#62; Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
