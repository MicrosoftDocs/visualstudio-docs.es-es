---
title: 'Cómo: buscar un contacto específico mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para buscar un contacto específico en Microsoft Outlook mediante programación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6813a137558a245c66d4b24deac07b1a6a77796a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524614"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Cómo: buscar un contacto específico mediante programación
  En este ejemplo se busca una carpeta de contactos de Outlook para un contacto específico por nombre y apellidos. En el ejemplo se supone que existe un contacto llamado **John Evans** en la carpeta Contactos.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Consulte también
- [Trabajar con elementos de contacto](../vsto/working-with-contact-items.md)
- [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
