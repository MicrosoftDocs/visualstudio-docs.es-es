---
title: 'Cómo: Dirigirse a la interfaz de usuario multilingüe de Office'
description: Obtenga información sobre cómo puede usar Visual Studio para dirigirse mediante programación a Microsoft Office interfaz de usuario multilingüe.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3cf838b544ec78c8c7d6e9e2d6f1cb747e999ccd
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823926"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>Cómo: Dirigirse a la interfaz de usuario multilingüe de Office
  El Interfaz de usuario multilingüe (es una característica Microsoft Office que ofrece al usuario final la capacidad de cambiar el idioma de la interfaz de usuario (UI). Por ejemplo, un usuario final que trabaja con una interfaz de usuario en inglés puede cambiar el idioma de la interfaz de usuario a español.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Si la aplicación la van a usar las personas que usan muchos idiomas de Office, puede agregar código para cambiar automáticamente el idioma de las cadenas de interfaz de usuario para que coincida con el idioma que usa Office en el equipo del usuario (si el usuario tiene instalados los recursos correctos).

## <a name="to-check-the-current-office-ui-setting"></a>Para comprobar la configuración actual de la interfaz de usuario de Office

1. Use la <xref:System.Threading.Thread.CurrentUICulture%2A> propiedad del subproceso actual. Establezca el idioma de las cadenas de interfaz de usuario para que coincida con el idioma usado por la versión de Office que se ejecuta actualmente en el equipo del usuario.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="see-also"></a>Consulte también
- [Cómo: Dirigir aplicaciones de Office a través de ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Enlace en tiempo de tarde en soluciones de Office](../vsto/late-binding-in-office-solutions.md)
