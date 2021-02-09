---
title: 'Cómo: buscar en una carpeta específica mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para buscar mediante programación en una carpeta específica de Microsoft Outlook.
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
ms.openlocfilehash: a9c7861698e678ca6d8332e3940c3ae49ff423f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877881"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Cómo: buscar en una carpeta específica mediante programación
  En este ejemplo de código `Find` se usan los `FindNext` métodos y para buscar texto en el campo asunto de los mensajes de correo electrónico que se encuentran en la **bandeja de entrada**. Este método usa un filtro de cadena para comprobar la letra T como la letra inicial del `Subject` texto.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Vea también
- [Trabajar con carpetas](../vsto/working-with-folders.md)
- [Información general del modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)
- [Cómo: recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
