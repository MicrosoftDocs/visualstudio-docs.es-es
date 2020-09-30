---
title: 'Cómo: buscar en una carpeta específica mediante programación'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f33b56da08fcd05706ac7681740cea04574d0070
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584747"
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
