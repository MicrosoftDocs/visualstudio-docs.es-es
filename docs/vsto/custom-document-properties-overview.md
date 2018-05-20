---
title: Información general sobre propiedades de documento personalizadas
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b85dfe077f73a26eadf173197de2ca514ff44679
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="custom-document-properties-overview"></a>Información general sobre propiedades de documento personalizadas

Cuando compila un proyecto de nivel de documento, Visual Studio agrega dos propiedades personalizadas al documento en el proyecto: \_AssemblyLocation y \_AssemblyName. Cuando un usuario abre un documento, la aplicación de Microsoft Office comprueba estas propiedades personalizadas del documento. Si existen en el documento, la aplicación carga el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], que inicia la personalización. Para obtener más información, consulte [soluciones de arquitectura de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="assemblyname"></a>\_AssemblyName

Esta propiedad contiene el CLSID de una interfaz en el componente de cargador de solución de Office de la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. El valor CLSID es 4E3C66D5 - 58D 4-491E-A7D4-64AF99AF6E8B. Nunca debe cambiar este valor.

## <a name="assemblylocation"></a>\_AssemblyLocation

Esta propiedad contiene una cadena que proporciona detalles sobre el manifiesto de implementación para la personalización. Para obtener más información sobre los manifiestos, consulte [manifiestos de aplicación e implementación de soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Valor de la propiedad The_AssemblyLocation puede tener formatos diferentes, dependiendo de cómo se implementa la solución:

- Si la solución se publica para que se instale desde un sitio Web, ruta de acceso UNC o una unidad de CD o USB, la propiedad _AssemblyLocation tiene el formato *rutaDeAccesoDelManifiestoDeImplementación*|*SolutionID*. La cadena siguiente es un ejemplo:

     File://deployserver/MyShare/ExcelWorkbook1.VSTO | 74744e4b-e4d6-41eb-84f7-ad20346fe2d9

- Si se ejecuta o depura la solución desde Visual Studio, la propiedad _AssemblyLocation tiene el formato *nombreDelManifiestoDeImplementación*|*SolutionID*| vstolocal. La cadena siguiente es un ejemplo:

     ExcelWorkbook1.vsto|74744e4b-e4d6-41eb-84f7-ad20346fe2d9 | vstolocal

 El *SolutionID* es un GUID que el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utiliza para identificar la solución. El *SolutionID* se genera automáticamente al compilar el proyecto. El **vstolocal** término indica a la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que se debe cargar el ensamblado desde la misma carpeta que el documento.

## <a name="see-also"></a>Vea también

- [Arquitectura de soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)
- [Manifiestos de aplicación e implementación de soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)
- [Cómo: publicar una solución de Office mediante ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)
- [Cómo: crear y modificar propiedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)
