---
title: 'Cómo: determinar el elemento actual de Outlook mediante programación'
description: Obtenga información sobre cómo puede determinar mediante programación el elemento actual de Microsoft Outlook. En este ejemplo se usa el evento Explorer. SelectionChange.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 720028528c036bf4485ca529f735fd26b1ff6e9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963840"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Cómo: determinar el elemento actual de Outlook mediante programación
  En este ejemplo se utiliza el `Explorer.SelectionChange` evento para mostrar el nombre de la carpeta actual y alguna información sobre el elemento seleccionado. Después, el código muestra el elemento seleccionado.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Elementos de citas, contactos y correo electrónico en Microsoft Office Outlook.

## <a name="see-also"></a>Vea también
- [Información general del modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)
- [Cómo: recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
