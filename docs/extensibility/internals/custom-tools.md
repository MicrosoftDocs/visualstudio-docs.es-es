---
title: Herramientas personalizadas ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708959"
---
# <a name="custom-tools"></a>Herramientas personalizadas
*Las herramientas personalizadas* le permiten asociar una herramienta con un elemento de un proyecto y ejecutarla siempre que se guarde el archivo. Ciertas herramientas personalizadas, a *veces denominadas generadores de*un solo archivo, se utilizan con frecuencia para implementar traductores que generan código a partir de datos y viceversa. Por ejemplo, los generadores [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] de un solo archivo crean y obtienen código fuente a partir de los archivos *.settings* y *.resx.* El código fuente generado proporciona acceso fuertemente tipado a los datos de los archivos *.settings* y *.resx.* Los [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipos y los de proyecto admiten herramientas personalizadas; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] los tipos de proyecto no lo hacen. Sus propios tipos de proyecto también pueden admitir herramientas personalizadas.

 Las herramientas personalizadas son `IVsSingleFileGenerator` componentes registrados que implementan la interfaz.

 Las herramientas personalizadas `ProjectItem` están asociadas a un objeto de interfaz y son como diseñadores y editores. Una herramienta personalizada toma el `ProjectItem` archivo representado por una como entrada y escribe `DefaultExtension` un nuevo archivo cuyo nombre de archivo es proporcionado por el método.

## <a name="in-this-section"></a>En esta sección
- [Implementar generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)

 Describe cómo usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> la interfaz para implementar una herramienta personalizada.

- [Registrar generadores de archivos individuales](../../extensibility/internals/registering-single-file-generators.md)

 Proporciona descripciones para todas las entradas del registro para una herramienta personalizada.

- [Exponer tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Explica cómo los sistemas de proyectos proporcionan compatibilidad para que los diseñadores visuales accedan a clases y tipos generados a través de archivos ejecutables portátiles temporales (PE).

- [Persistir la propiedad de un elemento de proyecto](../../extensibility/persisting-the-property-of-a-project-item.md)

 Muestra cómo conservar una propiedad de elemento de proyecto, como el autor de un archivo de origen, en el archivo de proyecto.

## <a name="reference"></a>Referencia
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Proporciona detalles <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>sobre el , que transforma un único archivo de entrada en un único archivo de salida que se puede compilar o agregar a un proyecto.

 <xref:EnvDTE.ProjectItem>Explica `ProjectItem` la interfaz, que representa un elemento de un proyecto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Proporciona detalles `DefaultExtension` sobre el método, que recupera la extensión de nombre de archivo que se proporciona al nombre de archivo de salida.

## <a name="related-sections"></a>Secciones relacionadas
- [Ampliar proyectos](../../extensibility/extending-projects.md)

 Describe cómo usar los proyectos y soluciones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para organizar los archivos de código y de recursos, así como la implementación del control de código fuente.
