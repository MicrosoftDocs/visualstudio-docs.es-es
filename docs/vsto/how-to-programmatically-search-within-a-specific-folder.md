---
title: Filtrar Buscar en una carpeta específica mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 5ac3dbb169fee82a55cc41b773d3616c56f83534
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638015"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Filtrar Buscar en una carpeta específica mediante programación
  Este ejemplo de código utiliza el `Find` y `FindNext` métodos para buscar texto en el campo de asunto de los mensajes de correo electrónico que se encuentran en el **Bandeja de entrada**. Este método utiliza un filtro de cadena para comprobar la letra T como la letra inicial de la `Subject` texto.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Vea también
- [Trabajar con carpetas](../vsto/working-with-folders.md)
- [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)
- [Cómo: Recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
