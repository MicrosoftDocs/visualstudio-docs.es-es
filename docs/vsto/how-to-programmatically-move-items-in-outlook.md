---
title: 'Cómo: trasladar elementos en Outlook mediante programación'
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
ms.openlocfilehash: 97f686a47d18fa91909de489f12f9c7a8c1306d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519917"
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

## <a name="see-also"></a>Vea también
- [Trabajar con carpetas](../vsto/working-with-folders.md)
- [Cómo: recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Cómo: buscar en una carpeta específica mediante programación](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Cómo: realizar acciones al recibir un mensaje de correo electrónico mediante programación](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
