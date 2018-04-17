---
title: 'Cómo: tener como destino la interfaz de usuario multilingüe de Office | Documentos de Microsoft'
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
ms.openlocfilehash: 54b305311b686f527a79092280fbc33c3974247e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Cómo: Apuntar a MUI (Multilingual User Interface, Interfaz de usuario multilingüe) de Office
  La interfaz de usuario multilingüe (MUI) es una característica de Microsoft Office que proporciona el usuario final la capacidad de cambiar el idioma de la interfaz de usuario (UI). Por ejemplo, un usuario final que trabaje con una interfaz de usuario inglés puede cambiar el idioma de la interfaz de usuario en español.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si va a utilizar la aplicación por personas que utilizan varios idiomas de Office, puede agregar código para cambiar automáticamente el idioma de las cadenas de interfaz de usuario para que coincida con el idioma que se va a utilizar por Office en el equipo del usuario (si el usuario tiene instalados los recursos correctos).  
  
### <a name="to-check-the-current-office-ui-setting"></a>Para comprobar la configuración actual de la interfaz de usuario de Office  
  
1.  Use la <xref:System.Threading.Thread.CurrentUICulture%2A> propiedad del subproceso actual. Establecer el idioma de las cadenas de interfaz de usuario para que coincida con el lenguaje utilizado por la versión de Office que se están ejecutando actualmente en el equipo del usuario.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md)  
  
  