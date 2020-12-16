---
title: 'Cómo: elegir como destino la interfaz de usuario multilingüe de Office'
description: Obtenga información sobre cómo puede usar Visual Studio para establecer como destino mediante programación la interfaz de usuario multilingüe de Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6b6771b202515148b757e811fdfc63fc0d5052e9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526624"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Cómo: elegir como destino la interfaz de usuario multilingüe de Office
  La interfaz de usuario multilingüe (MUI) es una característica Microsoft Office que proporciona al usuario final la capacidad de cambiar el idioma de la interfaz de usuario (UI). Por ejemplo, un usuario final que trabaja con una interfaz de usuario en inglés puede cambiar el idioma de la interfaz de usuario a español.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Si la aplicación va a ser utilizada por personas que usan muchos idiomas de Office, puede agregar código para cambiar automáticamente el idioma de las cadenas de la interfaz de usuario para que coincida con el idioma que usa Office en el equipo del usuario (si el usuario tiene instalados los recursos correctos).

## <a name="to-check-the-current-office-ui-setting"></a>Para comprobar la configuración actual de la interfaz de usuario de Office

1. Use la <xref:System.Threading.Thread.CurrentUICulture%2A> propiedad del subproceso actual. Establezca el idioma de las cadenas de la interfaz de usuario para que coincida con el idioma usado por la versión de Office que se ejecuta actualmente en el equipo del usuario.

     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]

## <a name="see-also"></a>Consulte también
- [Cómo: dirigirse a aplicaciones de Office a través de ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md)
