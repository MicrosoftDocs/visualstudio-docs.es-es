---
title: Configurar un equipo para desarrollar soluciones de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58458b51115834b5b94e858676ee8039d5894c70
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurar un equipo para desarrollar soluciones de Office

Para crear complementos y personalizaciones de VSTO para Microsoft Office, instale una versión compatible de Visual Studio, .NET Framework y Microsoft Office.

|Software|Versiones compatibles|
|--------------|------------------------|
|Visual Studio 2017| Cualquier edición con la **desarrollo de Office/SharePoint** carga de trabajo.|
|.NET Framework|-El .NET Framework 4 o posterior.|
|Microsoft Office|<ul><li>Cualquier edición de conjunto de Office, incluido Office Professional Plus para Office 365.</li><li>Cualquiera de las siguientes aplicaciones:<br /><br /> <ul><li>Excel</li><li>InfoPath (solo Office 2013 y Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Proyecto</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic para Aplicaciones (VBA) debe estar instalado como parte de Office. **Importante:** hacer clic para ejecutar versiones de aplicaciones de Office 2010 no son compatibles.|

Para obtener pasos de instalación detalladas, consulte [Cómo: configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Si las plantillas de proyecto no aparecen o no funcionan en Visual Studio

Si instala una versión compatible de Visual Studio, .NET Framework y Microsoft Office, pero las plantillas de proyecto de Office no aparecen en Visual Studio **nuevo proyecto** cuadro de diálogo, o si recibe un error al intentar usar uno, Compruebe lo siguiente:

- Asegúrese de que tiene Microsoft Office Developer Tools instalado en el equipo.

     Office Developer Tools es un componente opcional de Visual Studio, pero normalmente se instala automáticamente junto con Visual Studio. Si personaliza la instalación de Visual Studio y especifica las características que se deben instalar, asegúrese de elegir **Microsoft Office Developer Tools** durante la instalación.

     Para asegurarse de que estas herramientas se instalan, inicie el programa de instalación de Visual Studio y elija la **modificar** botón. Active la casilla **Microsoft Office Developer Tools** y después elija el botón **Actualizar** .

- Asegúrese de que no se está ejecutando una versión de Office entregada por medio de hacer clic en ejecutar. Vea [Cómo: comprobar si Outlook es una aplicación de hacer clic para ejecutar en un equipo](http://msdn.microsoft.com/library/office/ff864733(v=office.14).aspx).

- Asegúrese de que se ejecuta solo una versión de Microsoft Office.

Si sigue teniendo problemas, consulte [compatibilidad adicional para errores de soluciones de Office de](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Vea también

[Introducción &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)  
[Cómo: configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)  
[Cómo: instalar Visual Studio Tools para Office runtime redistribuible](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)  
[Cómo: instalar ensamblados de interoperabilidad primarios](../vsto/how-to-install-office-primary-interop-assemblies.md)  
[Características disponibles por tipo de aplicación y el proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md)
