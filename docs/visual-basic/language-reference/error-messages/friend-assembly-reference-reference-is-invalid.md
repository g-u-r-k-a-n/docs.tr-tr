---
description: 'Hakkında daha fazla bilgi edinin: BC31535: arkadaş derleme başvurusu <reference> geçersiz'
title: <reference> arkadaş derleme başvurusu geçersiz
ms.date: 07/20/2015
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords:
- BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
ms.openlocfilehash: e3e08edede9bee4710c415a61592857229ea4f35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796203"
---
# <a name="bc31535-friend-assembly-reference-reference-is-invalid"></a><span data-ttu-id="db9e5-103">BC31535: arkadaş derleme başvurusu \<reference> geçersiz</span><span class="sxs-lookup"><span data-stu-id="db9e5-103">BC31535: Friend assembly reference \<reference> is invalid</span></span>

<span data-ttu-id="db9e5-104">Arkadaş derleme başvurusu \<reference> geçersiz.</span><span class="sxs-lookup"><span data-stu-id="db9e5-104">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="db9e5-105">Tanımlayıcı adı imzalı derlemelerin InternalsVisibleTo bildirimlerinde bir ortak anahtar belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="db9e5-105">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>

 <span data-ttu-id="db9e5-106">Öznitelik oluşturucusuna geçirilen derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> , tanımlayıcı adlı bir derlemeyi tanımlar, ancak bir `PublicKey` özniteliği içermez.</span><span class="sxs-lookup"><span data-stu-id="db9e5-106">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>

 <span data-ttu-id="db9e5-107">**Hata kimliği:** BC31535</span><span class="sxs-lookup"><span data-stu-id="db9e5-107">**Error ID:** BC31535</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="db9e5-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="db9e5-108">To correct this error</span></span>

1. <span data-ttu-id="db9e5-109">Tanımlayıcı adlı Friend derlemesi için ortak anahtarı belirleme.</span><span class="sxs-lookup"><span data-stu-id="db9e5-109">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="db9e5-110">Özniteliği kullanılarak öznitelik oluşturucusuna geçirilen derleme adının bir parçası olarak ortak anahtarı ekleyin <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> `PublicKey` .</span><span class="sxs-lookup"><span data-stu-id="db9e5-110">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>

## <a name="see-also"></a><span data-ttu-id="db9e5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db9e5-111">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- [<span data-ttu-id="db9e5-112">Arkadaş derlemeleri</span><span class="sxs-lookup"><span data-stu-id="db9e5-112">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
