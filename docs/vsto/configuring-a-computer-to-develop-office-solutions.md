---
title: Configurar un equipo para desarrollar soluciones de Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e559ddfec8570077a78fe980632366b4a57605de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62930963"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurar un equipo para desarrollar soluciones de Office

Para crear complementos y personalizaciones de VSTO para Microsoft Office, instale una versión compatible de Visual Studio, .NET Framework y Microsoft Office.

|Software|Versiones compatibles|
|--------------|------------------------|
|Visual Studio 2017| Cualquier edición con el **desarrollo de Office/SharePoint** carga de trabajo.|
|.NET Framework|-.NET Framework 4 o posterior.|
|Microsoft Office|<ul><li>Cualquier edición de conjunto de Office, incluido Office Professional Plus para Office 365.</li><li>Cualquiera de las siguientes aplicaciones:<br /><br /> <ul><li>Excel</li><li>InfoPath (solo Office 2013 y Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Proyecto</li><li>Visio</li><li>Palabra</li></ul></li></ul><br /> Visual Basic para Aplicaciones (VBA) debe estar instalado como parte de Office. **Importante:** Las versiones Hacer clic y ejecutar de las aplicaciones de Office 2010 no son compatibles.|

Para conocer los pasos de instalación detalladas, consulte [Cómo: Configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Si no aparecen las plantillas de proyecto o no funcionan en Visual Studio

Si instala una versión compatible de Visual Studio, .NET Framework y Microsoft Office, pero las plantillas de proyecto de Office no aparecen en Visual Studio **nuevo proyecto** cuadro de diálogo, o si recibe un error al intentar usar uno, Compruebe lo siguiente:

- Asegúrese de que tiene Microsoft Office Developer Tools instalado en el equipo.

     Office developer tools son un componente opcional de Visual Studio, pero se instalan automáticamente junto con Visual Studio. Si personaliza la instalación de Visual Studio y especifica las características que se deben instalar, asegúrese de elegir **Microsoft Office Developer Tools** durante la instalación.

     Para asegurarse de que estas herramientas están instaladas, inicie el programa de instalación de Visual Studio y elija el **modificar** botón. Active la casilla **Microsoft Office Developer Tools** y después elija el botón **Actualizar** .

- Asegúrese de que no está ejecutando una versión de Office entregada por medio de hacer clic en ejecutar. Vea [Cómo: Comprobar si Outlook es una aplicación de hacer clic para ejecutar en un equipo](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Asegúrese de que está ejecutando una sola versión de Microsoft Office.

Si sigue teniendo problemas, vea [compatibilidad adicional para errores en soluciones de Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Vea también
- [Introducción a &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Cómo: Configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Cómo: Instalar Visual Studio Tools para Office runtime redistribuible](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Cómo: Instalar a ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Características disponibles por tipo de aplicación y el proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md)