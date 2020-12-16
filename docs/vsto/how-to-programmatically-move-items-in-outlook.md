---
title: 'Cómo: trasladar elementos en Outlook mediante programación'
description: Obtenga información sobre cómo puede trasladar elementos en Microsoft Outlook mediante programación. En este ejemplo se mueven los mensajes de correo electrónico sin leer de la bandeja de entrada a una carpeta denominada test.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b247df68827767a53d8d066f4750dfa9da52ac7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525573"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Cómo: trasladar elementos en Outlook mediante programación
  En este ejemplo se mueven los mensajes de correo electrónico sin leer de la **bandeja de entrada** a una carpeta denominada **Test**. En el ejemplo solo se mueven los mensajes que tienen la palabra **Test** en el `Subject` campo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo se necesita:

- Una carpeta de correo de Outlook denominada **Test**.

- Un mensaje de correo electrónico que llega con la palabra **Test** en el `Subject` campo.

## <a name="see-also"></a>Consulte también
- [Trabajar con carpetas](../vsto/working-with-folders.md)
- [Cómo: recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: buscar en una carpeta específica mediante programación](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Cómo: realizar acciones al recibir un mensaje de correo electrónico mediante programación](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
