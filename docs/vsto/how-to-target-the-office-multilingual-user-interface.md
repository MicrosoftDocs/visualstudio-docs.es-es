---
title: 'Cómo: tener como destino la interfaz de usuario multilingüe de Office'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1b917479598b73f71a0f3092c874276a700717d6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Cómo: tener como destino la interfaz de usuario multilingüe de Office
  La interfaz de usuario multilingüe (MUI) es una característica de Microsoft Office que proporciona el usuario final la capacidad de cambiar el idioma de la interfaz de usuario (UI). Por ejemplo, un usuario final que trabaje con una interfaz de usuario inglés puede cambiar el idioma de la interfaz de usuario en español.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si va a utilizar la aplicación por personas que usan muchos lenguajes de Office, puede agregar código para cambiar automáticamente el idioma de las cadenas de interfaz de usuario para que coincida con el idioma que se va a utilizar por Office en el equipo del usuario (si el usuario tiene instalados los recursos correctos).  
  
## <a name="to-check-the-current-office-ui-setting"></a>Para comprobar la configuración actual de la interfaz de usuario de Office  
  
1.  Use la <xref:System.Threading.Thread.CurrentUICulture%2A> propiedad del subproceso actual. Establecer el idioma de las cadenas de interfaz de usuario para que coincida con el idioma utilizado por la versión de Office que actualmente se ejecuta en el equipo del usuario.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: las aplicaciones de Office de destino a través de los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Enlace tardío en soluciones de Office](../vsto/late-binding-in-office-solutions.md)  
  
  