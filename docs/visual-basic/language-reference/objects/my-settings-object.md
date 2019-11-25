---
title: My.Settings Nesnesi
ms.date: 07/20/2015
f1_keywords:
- My.MySettingsProperty.Settings
- My.Settings
helpviewer_keywords:
- My.Settings object
ms.assetid: 41f30dc1-202a-4273-b9b7-5728941f996c
ms.openlocfilehash: 9560a51332ea596d4cf2228f1e07c158a0457ece
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350354"
---
# <a name="mysettings-object"></a><span data-ttu-id="a5256-102">My.Settings Nesnesi</span><span class="sxs-lookup"><span data-stu-id="a5256-102">My.Settings Object</span></span>
<span data-ttu-id="a5256-103">Provides properties and methods for accessing the application's settings.</span><span class="sxs-lookup"><span data-stu-id="a5256-103">Provides properties and methods for accessing the application's settings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5256-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5256-104">Remarks</span></span>  
 <span data-ttu-id="a5256-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span><span class="sxs-lookup"><span data-stu-id="a5256-105">The `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application.</span></span> <span data-ttu-id="a5256-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a5256-106">For more information, see [Managing Application Settings (.NET)](/visualstudio/ide/managing-application-settings-dotnet).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a5256-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a5256-107">Properties</span></span>  
 <span data-ttu-id="a5256-108">The properties of the `My.Settings` object provide access to your application's settings.</span><span class="sxs-lookup"><span data-stu-id="a5256-108">The properties of the `My.Settings` object provide access to your application's settings.</span></span> <span data-ttu-id="a5256-109">To add or remove settings, use the **Settings Designer**.</span><span class="sxs-lookup"><span data-stu-id="a5256-109">To add or remove settings, use the **Settings Designer**.</span></span>  
  
 <span data-ttu-id="a5256-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span><span class="sxs-lookup"><span data-stu-id="a5256-110">Each setting has a **Name**, **Type**, **Scope**, and **Value**, and these settings determine how the property to access each setting appears in the `My.Settings` object:</span></span>  
  
- <span data-ttu-id="a5256-111">**Name** determines the name of the property.</span><span class="sxs-lookup"><span data-stu-id="a5256-111">**Name** determines the name of the property.</span></span>  
  
- <span data-ttu-id="a5256-112">**Type** determines the type of the property.</span><span class="sxs-lookup"><span data-stu-id="a5256-112">**Type** determines the type of the property.</span></span>  
  
- <span data-ttu-id="a5256-113">**Scope** indicates if the property is read-only.</span><span class="sxs-lookup"><span data-stu-id="a5256-113">**Scope** indicates if the property is read-only.</span></span> <span data-ttu-id="a5256-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span><span class="sxs-lookup"><span data-stu-id="a5256-114">If the value is **Application**, the property is read-only; if the value is **User**, the property is read-write.</span></span>  
  
- <span data-ttu-id="a5256-115">**Value** is the default value of the property.</span><span class="sxs-lookup"><span data-stu-id="a5256-115">**Value** is the default value of the property.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5256-116">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a5256-116">Methods</span></span>  
  
|<span data-ttu-id="a5256-117">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a5256-117">Method</span></span>|<span data-ttu-id="a5256-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5256-118">Description</span></span>|  
|---|---|  
|`Reload`|<span data-ttu-id="a5256-119">Reloads the user settings from the last saved values.</span><span class="sxs-lookup"><span data-stu-id="a5256-119">Reloads the user settings from the last saved values.</span></span>|  
|`Save`|<span data-ttu-id="a5256-120">Saves the current user settings.</span><span class="sxs-lookup"><span data-stu-id="a5256-120">Saves the current user settings.</span></span>|  
  
 <span data-ttu-id="a5256-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span><span class="sxs-lookup"><span data-stu-id="a5256-121">The `My.Settings` object also provides advanced properties and methods, inherited from the <xref:System.Configuration.ApplicationSettingsBase> class.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="a5256-122">Görevler</span><span class="sxs-lookup"><span data-stu-id="a5256-122">Tasks</span></span>  
 <span data-ttu-id="a5256-123">The following table lists examples of tasks involving the `My.Settings` object.</span><span class="sxs-lookup"><span data-stu-id="a5256-123">The following table lists examples of tasks involving the `My.Settings` object.</span></span>  
  
|<span data-ttu-id="a5256-124">Bitiş</span><span class="sxs-lookup"><span data-stu-id="a5256-124">To</span></span>|<span data-ttu-id="a5256-125">Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5256-125">See</span></span>|  
|---|---|  
|<span data-ttu-id="a5256-126">Read an application setting</span><span class="sxs-lookup"><span data-stu-id="a5256-126">Read an application setting</span></span>|[<span data-ttu-id="a5256-127">How to: Read Application Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5256-127">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)|  
|<span data-ttu-id="a5256-128">Change a user setting</span><span class="sxs-lookup"><span data-stu-id="a5256-128">Change a user setting</span></span>|[<span data-ttu-id="a5256-129">How to: Change User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5256-129">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)|  
|<span data-ttu-id="a5256-130">Persist user settings</span><span class="sxs-lookup"><span data-stu-id="a5256-130">Persist user settings</span></span>|[<span data-ttu-id="a5256-131">How to: Persist User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5256-131">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)|  
|<span data-ttu-id="a5256-132">Create a property grid for user settings</span><span class="sxs-lookup"><span data-stu-id="a5256-132">Create a property grid for user settings</span></span>|[<span data-ttu-id="a5256-133">How to: Create Property Grids for User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5256-133">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)|  
  
## <a name="example"></a><span data-ttu-id="a5256-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5256-134">Example</span></span>  
 <span data-ttu-id="a5256-135">This example displays the value of the `Nickname` setting.</span><span class="sxs-lookup"><span data-stu-id="a5256-135">This example displays the value of the `Nickname` setting.</span></span>  
  
 [!code-vb[VbVbalrMyResources#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#14)]  
  
 <span data-ttu-id="a5256-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span><span class="sxs-lookup"><span data-stu-id="a5256-136">For this example to work, your application must have a `Nickname` setting, of type `String`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5256-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5256-137">See also</span></span>

- <xref:System.Configuration.ApplicationSettingsBase>
- [<span data-ttu-id="a5256-138">How to: Read Application Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5256-138">How to: Read Application Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [<span data-ttu-id="a5256-139">How to: Change User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5256-139">How to: Change User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [<span data-ttu-id="a5256-140">How to: Persist User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5256-140">How to: Persist User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [<span data-ttu-id="a5256-141">How to: Create Property Grids for User Settings in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5256-141">How to: Create Property Grids for User Settings in Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)
- [<span data-ttu-id="a5256-142">Uygulama Ayarlarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="a5256-142">Managing Application Settings (.NET)</span></span>](/visualstudio/ide/managing-application-settings-dotnet)
