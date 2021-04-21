---
title: 'Cómo: Mover elementos mediante programación en Outlook'
description: Obtenga información sobre cómo puede mover elementos mediante programación en Microsoft Outlook. En este ejemplo se mueven mensajes de correo electrónico no leídos de la Bandeja de entrada a una carpeta denominada Prueba.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b8e951ab393d09506ad4f2d593962ea1826eff09
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826738"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Cómo: Mover elementos mediante programación en Outlook
  En este ejemplo se mueven mensajes de correo electrónico no leídos de la **Bandeja de entrada** a una carpeta denominada **Test**. En el ejemplo solo se mueven los mensajes que tienen la palabra **Test** en el `Subject` campo .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Una carpeta de correo de Outlook denominada **Test**.

- Mensaje de correo electrónico que llega con la palabra **Prueba** en el `Subject` campo.

## <a name="see-also"></a>Consulte también
- [Trabajar con carpetas](../vsto/working-with-folders.md)
- [Cómo: Recuperar mediante programación una carpeta por nombre](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: Buscar mediante programación dentro de una carpeta específica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Cómo: Realizar acciones mediante programación cuando se recibe un mensaje de correo electrónico](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
