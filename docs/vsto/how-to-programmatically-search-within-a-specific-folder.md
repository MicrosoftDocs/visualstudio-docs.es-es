---
title: 'Cómo: Buscar mediante programación dentro de una carpeta específica'
description: Obtenga información sobre cómo puede usar Visual Studio para buscar mediante programación dentro de una carpeta específica de Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b25880420e23b82f6f63ab28ef5f1f93429bdd8c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824762"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Cómo: Buscar mediante programación dentro de una carpeta específica
  En este ejemplo de código se usan los métodos y para buscar texto en el campo de asunto de los mensajes de correo electrónico que `Find` se encuentran en la bandeja de `FindNext` **entrada**. Este método usa un filtro de cadena para buscar la letra T como letra inicial del `Subject` texto.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Consulte también
- [Trabajar con carpetas](../vsto/working-with-folders.md)
- [Introducción al modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)
- [Cómo: Recuperar mediante programación una carpeta por nombre](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
