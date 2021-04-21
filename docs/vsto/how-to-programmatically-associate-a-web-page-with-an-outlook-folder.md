---
title: Asociación de una página web a una carpeta de Outlook
description: Obtenga información sobre cómo puede asociar una página web a Microsoft Office carpeta outlook. En este ejemplo se comprueba si hay una carpeta denominada HtmlView en Outlook.
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
ms.openlocfilehash: 3f022deca9b8cd1b8f00bf847ab0bfdc7882a45f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828272"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Asociación de una página web a una carpeta de Outlook

  En este ejemplo se comprueba si hay una carpeta `HtmlView` denominada en Microsoft Office Outlook. Si la carpeta no existe, el código crea la carpeta y le asigna una página web. Si la carpeta existe, el código muestra el contenido de la carpeta.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Consulte también
- [Trabajar con carpetas](../vsto/working-with-folders.md)
- [Cómo: Recuperar mediante programación una carpeta por nombre](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: Crear elementos de carpeta personalizados mediante programación](../vsto/how-to-programmatically-create-custom-folder-items.md)
