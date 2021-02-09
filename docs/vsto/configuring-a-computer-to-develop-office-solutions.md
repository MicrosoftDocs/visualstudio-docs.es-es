---
title: Configurar un equipo para desarrollar soluciones de Office
description: Obtenga información sobre cómo puede instalar una versión compatible de Visual Studio, la .NET Framework y Microsoft Office para poder crear complementos y personalizaciones de VSTO para Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, installing tools
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ee8f840aa81d3decfdb96dd2658b758704443347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910574"
---
# <a name="configure-a-computer-to-develop-office-solutions"></a>Configurar un equipo para desarrollar soluciones de Office

Para crear complementos y personalizaciones de VSTO para Microsoft Office, instale una versión compatible de Visual Studio, .NET Framework y Microsoft Office.

|Software|Versiones compatibles|
|--------------|------------------------|
|Visual Studio 2017| Cualquier edición con la carga de trabajo **desarrollo de Office/SharePoint** .|
|.NET Framework|-El .NET Framework 4 o posterior.|
|Microsoft Office|<ul><li>Cualquier edición de conjunto de Office, incluidas Microsoft 365 aplicaciones para empresas.</li><li>Cualquiera de las siguientes aplicaciones:<br /><br /> <ul><li>Excel</li><li>InfoPath (solo Office 2013 y Office 2010)</li><li>Outlook</li><li>PowerPoint</li><li>Project</li><li>Visio</li><li>Word</li></ul></li></ul><br /> Visual Basic para Aplicaciones (VBA) debe estar instalado como parte de Office. **Importante:** No se admiten las versiones de hacer clic y ejecutar de Office 2010.|

Para obtener pasos de instalación detallados, consulte [Cómo: configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md).

## <a name="if-project-templates-dont-appear-or-they-dont-work-in-visual-studio"></a>Si las plantillas de proyecto no aparecen o no funcionan en Visual Studio

Si instala una versión compatible de Visual Studio, el .NET Framework, y Microsoft Office, pero las plantillas de proyecto de Office no aparecen en el cuadro de diálogo **nuevo proyecto** de Visual Studio o recibe un error al intentar usar una, compruebe lo siguiente:

- Asegúrese de que tiene Microsoft Office Developer Tools instalado en el equipo.

     Office Developer Tools es un componente opcional de Visual Studio, pero se instalan automáticamente junto con Visual Studio. Si personaliza la instalación de Visual Studio y especifica las características que se deben instalar, asegúrese de elegir **Microsoft Office Developer Tools** durante la instalación.

     Para asegurarse de que estas herramientas están instaladas, inicie el programa de instalación de Visual Studio y elija el botón **modificar** . Active la casilla **Microsoft Office Developer Tools** y después elija el botón **Actualizar** .

- Asegúrese de que no está ejecutando una versión de Office ofrecida por hacer clic y ejecutar. Vea [Cómo: comprobar si Outlook es una aplicación de hacer clic y ejecutar en un equipo](/previous-versions/office/developer/office-2010/ff864733(v=office.14)).

- Asegúrese de que está ejecutando solo una versión de Microsoft Office.

Si sigue teniendo problemas, consulte [Compatibilidad adicional con errores en las soluciones de Office](../vsto/additional-support-for-errors-in-office-solutions.md).

## <a name="see-also"></a>Vea también
- [Introducción &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Cómo: configurar un equipo para desarrollar soluciones de Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Cómo: instalar el Visual Studio Tools para Office Runtime Redistributable](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)
- [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md)