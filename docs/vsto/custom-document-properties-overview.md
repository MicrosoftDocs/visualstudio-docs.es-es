---
title: Información general sobre propiedades personalizadas del documento
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], custom properties
- custom document properties
- document-level customizations [Office development in Visual Studio], custom properties
- Office documents [Office development in Visual Studio], custom properties
- _AssemblyLocation property
- _AssemblyName property
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b3f4038a05478d8e2d747efa700c7ece02e4827
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62951174"
---
# <a name="custom-document-properties-overview"></a>Información general sobre propiedades personalizadas del documento

Al compilar un proyecto de nivel de documento, Visual Studio agrega dos propiedades personalizadas al documento en el proyecto: \_ AssemblyLocation y \_ AssemblyName. Cuando un usuario abre un documento, la aplicación Microsoft Office comprueba estas propiedades de documento personalizadas. Si existen en el documento, la aplicación carga [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , lo que inicia la personalización. Para obtener más información, vea [arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="_assemblyname"></a>\_NombreDeEnsamblado

Esta propiedad contiene el CLSID de una interfaz en el componente del cargador de soluciones de Office de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . El valor CLSID es 4E3C66D5-58D4-491E-A7D4-64AF99AF6E8B. Nunca debe cambiar este valor.

## <a name="_assemblylocation"></a>\_AssemblyLocation

Esta propiedad contiene una cadena que proporciona detalles sobre el manifiesto de implementación para la personalización. Para obtener más información sobre los manifiestos, vea [manifiestos de aplicación e implementación en las soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 El \_ valor de la propiedad AssemblyLocation puede tener distintos formatos, en función de cómo se implemente la solución:

- Si la solución se publica para instalarse desde un sitio web, una ruta de acceso UNC o una unidad de CD o USB, la propiedad _AssemblyLocation tiene el formato *DeploymentManifestPath* | *SolutionID*. La siguiente cadena es un ejemplo:

     file://deployserver/MyShare/ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Si está ejecutando o depurando la solución desde Visual Studio, la propiedad _AssemblyLocation tiene el formato *DeploymentManifestName* | *SolutionID*| vstolocal. La siguiente cadena es un ejemplo:

     ExcelWorkbook1. VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

  *SolutionID* es un GUID que [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usa para identificar la solución. El *SolutionID* se genera automáticamente al compilar el proyecto. El término **vstolocal** indica a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que el ensamblado se debe cargar desde la misma carpeta que el documento.

## <a name="see-also"></a>Consulte también

- [Arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)
- [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Cómo: publicar una solución de Office mediante ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Cómo: crear y modificar propiedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)
