---
title: Procedimiento Destino de la interfaz de usuario multilingüe de Office
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5180780835f36768cef77207189a1346c1dccdca
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866521"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Procedimiento Destino de la interfaz de usuario multilingüe de Office
  La interfaz de usuario multilingüe (MUI) es una característica de Microsoft Office que proporciona al usuario final la capacidad de cambiar el idioma de la interfaz de usuario (UI). Por ejemplo, un usuario final, trabajando con una interfaz de usuario inglés puede cambiar el idioma de la interfaz de usuario en español.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si la aplicación se usará por personas que utilizan muchos idiomas de Office, puede agregar código para cambiar automáticamente el idioma de las cadenas de interfaz de usuario para que coincida con el idioma que utiliza Office en el equipo del usuario (si el usuario tiene instalados los recursos correctos).  
  
## <a name="to-check-the-current-office-ui-setting"></a>Para comprobar la configuración actual de la interfaz de usuario de Office  
  
1.  Use el <xref:System.Threading.Thread.CurrentUICulture%2A> propiedad del subproceso actual. Establecer el idioma de las cadenas de interfaz de usuario para que coincida con el idioma usado por la versión de Office que actualmente se ejecuta en el equipo del usuario.  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Aplicaciones de Office de destino a través de los ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Enlace en tiempo de ejecución en las soluciones de Office](../vsto/late-binding-in-office-solutions.md)  
