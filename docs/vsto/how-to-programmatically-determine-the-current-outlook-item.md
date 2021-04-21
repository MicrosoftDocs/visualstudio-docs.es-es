---
title: 'Cómo: Determinar mediante programación el elemento actual de Outlook'
description: Obtenga información sobre cómo puede determinar mediante programación el elemento actual de Microsoft Outlook. En este ejemplo se usa el evento Explorer.SelectionChange.
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
ms.openlocfilehash: 9cddc4bdc99e97c12a04e57639f990a1484c6581
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823936"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Cómo: Determinar mediante programación el elemento actual de Outlook
  En este ejemplo se `Explorer.SelectionChange` usa el evento para mostrar el nombre de la carpeta actual y cierta información sobre el elemento seleccionado. A continuación, el código muestra el elemento seleccionado.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Citas, contactos y elementos de correo electrónico en Microsoft Office Outlook.

## <a name="see-also"></a>Consulte también
- [Introducción al modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)
- [Cómo: Recuperar mediante programación una carpeta por nombre](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: Buscar mediante programación un contacto específico](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
