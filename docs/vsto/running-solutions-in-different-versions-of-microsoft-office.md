---
title: Ejecutar soluciones en diferentes versiones de Microsoft Office
description: Obtenga información sobre cómo puede ejecutar versiones de Microsoft Office soluciones creadas con Visual Studio 2010 y versiones posteriores.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], multiple Office versions
- Office applications [Office development in Visual Studio], multiple Office versions
- Office development in Visual Studio, multiple Office versions
- Office solutions [Office development in Visual Studio]
- multiple Office versions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d70e61e318f0f6afd0a58ed35f912b6a5f2cda8
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523547"
---
# <a name="run-solutions-in-different-versions-of-microsoft-office"></a>Ejecutar soluciones en diferentes versiones de Microsoft Office

## <a name="run-office-solutions-created-by-using-visual-studio-2010-and-above"></a>Ejecutar soluciones de Office creadas con Visual Studio 2010 y versiones posteriores

|Versión de Office establecida como destino por la plantilla de proyecto|.NET Framework de destino del proyecto<sup>1</sup>|Versiones de Office que pueden ejecutar la solución|Tiempo de ejecución necesario en el equipo del usuario final|
|--------------------------------------------------------|------------------------------------------------------|--------------------------------------------------|-------------------------------------------|
|Office 2016 y [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistema<sup>2</sup>|Visual Studio 2010 Tools para Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> 2007 Microsoft Office sistema<sup>2</sup>|Visual Studio 2010 Tools para Office Runtime|
|[!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|.NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]|Visual Studio 2010 Tools para Office Runtime|
|Microsoft Office System 2007|[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores,<br /><br /> o<br /><br /> .NET Framework 3.5|Office 2016<br /><br /> [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]<br /><br /> [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<br /><br /> Microsoft Office System 2007|Visual Studio 2010 Tools para Office Runtime|

 1. La versión de .NET Framework que tiene como destino el proyecto es necesaria en los equipos de los usuarios finales para que la solución se ejecute. Por ejemplo, si el proyecto tiene como destino el .NET Framework 3,5, el .NET Framework 3,5 es necesario en los equipos de los usuarios finales. En este ejemplo, la solución no se ejecutará si solo [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] está instalado en los equipos de los usuarios finales.

 2. En este escenario, la solución solo se ejecutará sin errores en 2007 Microsoft Office system si no utiliza las características que son nuevas en [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

## <a name="run-office-solutions-created-by-using-versions-of-visual-studio-prior-to-visual-studio-2010"></a>Ejecutar soluciones de Office creadas con versiones de Visual Studio anteriores a Visual Studio 2010
 Las aplicaciones de Microsoft Office pueden ejecutar soluciones de Office creadas con versiones de Visual Studio anteriores a Visual Studio 2010. En algunos casos, estas soluciones requieren versiones diferentes de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Se pueden instalar diferentes versiones de en paralelo en el mismo equipo.

 En la tabla siguiente se muestran las versiones de Microsoft Office pueden ejecutar soluciones creadas con versiones anteriores de Visual Studio y qué versiones de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] y el .NET Framework son necesarias para cada solución.

|Edición de Visual Studio utilizada para crear la solución|Versión de Office establecida como destino por la plantilla de proyecto|Versiones de Office que pueden ejecutar la solución|Tiempo de ejecución necesario en el equipo del usuario final|Versión de .NET Framework necesaria en el equipo del usuario final|
|----------------------------------------------------------|--------------------------------------------------------|--------------------------------------------------|-------------------------------------------|----------------------------------------------------------|
|Visual Studio 2008 Professional<br /><br /> o<br /><br /> Visual Studio Team System 2008|Microsoft Office System 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]<sup>1</sup><br /><br /> Microsoft Office System 2007|Visual Studio 2010 Tools para Office Runtime<sup>1</sup><br /><br /> o<br /><br /> Visual Studio Tools para Microsoft Office System (versión 3.0 Runtime)|.NET Framework 3.5|
|Una de las siguientes ediciones de Visual Studio 2005 con VSTO 2005 SE<sup>2</sup> instalada:<br /><br /> -Visual Studio 2005 Tools para Office<br />-Visual Studio Team System 2005<br />-Visual Studio 2005 Professional|Microsoft Office System 2007|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (solo 32 bits<sup>3</sup>)<br /><br /> Microsoft Office System 2007|Runtime de Visual Studio 2005 Tools para Office Second Edition|.NET Framework 2.0, .NET Framework 3.0 o .NET Framework 3.5|
|Cualquiera de las siguientes ediciones de Visual Studio:<br /><br /> -Visual Studio 2008 Professional<br />-Visual Studio Team System 2008<br />-Visual Studio 2005 Tools para Office (con o sin VSTO 2005 SE<sup>2</sup> instalado)<br />-Visual Studio Team System 2005 (con o sin VSTO 2005 SE<sup>2</sup> instalado)<br />-Visual Studio 2005 Professional con VSTO 2005 SE<sup>2</sup> instalado|Microsoft Office 2003|[!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] (solo 32 bits<sup>3</sup>)<br /><br /> Microsoft Office System 2007<br /><br /> Microsoft Office 2003|Runtime de Visual Studio 2005 Tools para Office Second Edition|.NET Framework 2.0, .NET Framework 3.0 o .NET Framework 3.5|

 1. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] las [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplicaciones de y incluyen el motor en tiempo de ejecución de Visual Studio 2010 Tools para Office. Por lo tanto, estas aplicaciones siempre usan el motor en tiempo de ejecución de Visual Studio 2010 Tools para Office en lugar de la Visual Studio Tools para el sistema de Microsoft Office (versión 3,0 en tiempo de ejecución) en este escenario. Las aplicaciones de 2007 Microsoft Office system pueden usar el Runtime de Visual Studio 2010 Tools para Office o Visual Studio Tools para Microsoft Office system (versión 3.0 Runtime).

 2. VSTO 2005 SE es un complemento gratuito de Visual Studio que proporciona plantillas de proyecto de complementos de VSTO para Microsoft Office 2003 y 2007 Microsoft Office system. Se puede instalar con Visual Studio 2005 Professional, Visual Studio 2005 Tools para Office o una edición de Visual Studio Team System 2005. Para obtener más información, vea [Visual Studio 2005 Tools para Office Second Edition](https://developer.microsoft.com/office/docs).

 3. Las soluciones de Office que requieren Visual Studio 2005 Tools para Office Second Edition Runtime no son compatibles con las versiones de 64 bits de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] y [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]. Para ejecutar estas soluciones en la edición de 64 bits de [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], debe actualizar el proyecto a [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] o a un proyecto de Visual Studio 2008 que tenga establecido 2007 Microsoft Office system como destino.

## <a name="see-also"></a>Consulte también
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Información general sobre el tiempo de ejecución de Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio Tools para escenarios de instalación en tiempo de ejecución de Office](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Configurar un equipo para desarrollar soluciones de Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md)
