---
title: Herramientas personalizadas | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708959"
---
# <a name="custom-tools"></a>Herramientas personalizadas
*Las herramientas personalizadas* permiten asociar una herramienta a un elemento de un proyecto y ejecutar esa herramienta cada vez que se guarda el archivo. Ciertas herramientas personalizadas, que a veces se denominan *generadores de un solo archivo*, se usan con frecuencia para implementar traductores que generan código a partir de datos y viceversa. Por ejemplo, los generadores de un solo archivo crean [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] código fuente de los archivos *. Settings* y *. resx* . El código fuente generado proporciona acceso fuertemente tipado a los datos de los archivos *. Settings* y *. resx* . Los [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipos de proyecto y admiten herramientas personalizadas; los [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tipos de proyecto no. Sus propios tipos de proyecto también pueden admitir herramientas personalizadas.

 Las herramientas personalizadas son componentes registrados que implementan la `IVsSingleFileGenerator` interfaz.

 Las herramientas personalizadas están asociadas a un `ProjectItem` objeto de interfaz y son similares a los diseñadores y editores. Una herramienta personalizada toma el archivo representado por `ProjectItem` como entrada y escribe un archivo nuevo cuyo nombre de archivo lo proporciona el `DefaultExtension` método.

## <a name="in-this-section"></a>En esta sección
- [Implementar generadores de un solo archivo](../../extensibility/internals/implementing-single-file-generators.md)

 Describe cómo utilizar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz para implementar una herramienta personalizada.

- [Registro de generadores de un solo archivo](../../extensibility/internals/registering-single-file-generators.md)

 Proporciona descripciones de todas las entradas del registro de una herramienta personalizada.

- [Exponer tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Explica cómo los sistemas de proyecto proporcionan compatibilidad para que los diseñadores visuales tengan acceso a clases y tipos generados a través de archivos ejecutables portables (PE).

- [Conservar la propiedad de un elemento de proyecto](../../extensibility/persisting-the-property-of-a-project-item.md)

 Muestra cómo conservar una propiedad de elemento de proyecto, como el autor de un archivo de código fuente, en el archivo de proyecto.

## <a name="reference"></a>Referencia
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> Proporciona detalles sobre el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> , que transforma un único archivo de entrada en un único archivo de salida que se puede compilar o agregar a un proyecto de.

 <xref:EnvDTE.ProjectItem> Explica la `ProjectItem` interfaz, que representa un elemento de un proyecto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> Proporciona detalles sobre el `DefaultExtension` método, que recupera la extensión de nombre de archivo que se proporciona al nombre del archivo de salida.

## <a name="related-sections"></a>Secciones relacionadas
- [Ampliar proyectos](../../extensibility/extending-projects.md)

 Describe cómo usar los proyectos y soluciones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para organizar los archivos de código y de recursos, así como la implementación del control de código fuente.
