---
title: Asociar una página web a una carpeta de Outlook
description: Obtenga información sobre cómo puede asociar una página web con Microsoft Office carpeta de Outlook. En este ejemplo se comprueba si hay una carpeta denominada HtmlView en Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 35fad43f78d654cfaf9e06c1f432c620da830dd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885578"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Asociar una página web a una carpeta de Outlook

  En este ejemplo se comprueba si hay una carpeta denominada `HtmlView` en Microsoft Office Outlook. Si la carpeta no existe, el código crea la carpeta y le asigna una página web. Si la carpeta existe, el código muestra el contenido de la carpeta.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Vea también
- [Trabajar con carpetas](../vsto/working-with-folders.md)
- [Cómo: recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: crear elementos de carpeta personalizados mediante programación](../vsto/how-to-programmatically-create-custom-folder-items.md)
