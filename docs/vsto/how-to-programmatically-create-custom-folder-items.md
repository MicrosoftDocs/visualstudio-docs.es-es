---
title: 'Cómo: crear elementos de carpeta personalizados mediante programación'
description: Obtenga información sobre cómo puede crear elementos de carpeta personalizados mediante programación en Microsoft Outlook mediante Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], creating
- Outlook folders [Office development in Visual Studio], custom
author: John-Hart
ms.author: johnhart
ms.workload:
- office
ms.openlocfilehash: f149758665e5d7a7cdf7f4edd5d926e1de632dca
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527789"
---
# <a name="how-to-programmatically-create-custom-folder-items"></a>Cómo: crear elementos de carpeta personalizados mediante programación
  En este ejemplo se crea una nueva carpeta en Microsoft Office Outlook. El nombre del usuario que ha iniciado sesión se usa para el nombre de la carpeta.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_OL_CustFolderItem#1](../vsto/codesnippet/CSharp/Trin_OL_CustFolderItem/thisaddin.cs#1)]

## <a name="see-also"></a>Consulte también
- [Trabajar con carpetas](../vsto/working-with-folders.md)
- [Cómo: agregar una entrada a contactos de Outlook mediante programación](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Cómo: crear citas mediante programación](../vsto/how-to-programmatically-create-appointments.md)
