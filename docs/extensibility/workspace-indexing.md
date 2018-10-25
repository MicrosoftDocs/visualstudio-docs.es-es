---
title: Área de trabajo de indexación en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939155"
---
# <a name="workspace-indexing"></a>Área de trabajo de indexación

En una solución, los sistemas de proyectos son responsables de proporcionar funcionalidad de compilación, depuración, **GoTo** buscar símbolos y mucho más. Sistemas del proyecto pueden hacer este trabajo, porque entienden las capacidades de archivos dentro de un proyecto y la relación. Un [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) área de trabajo necesita la misma información para proporcionar características del IDE enriquecidas también. La recopilación y el almacenamiento persistente de los datos es un proceso llamado el área de trabajo de indexación. Estos datos indizados pueden consultarse a través de un conjunto de API asincrónicas. Los extensores pueden participar en el proceso de indización proporcionando <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>s que sepa cómo controlar ciertos tipos de archivos.

## <a name="types-of-indexed-data"></a>Tipos de datos indizados

Hay tres tipos de datos que se indizan. Tenga en cuenta el tipo esperado de los escáneres de archivo diferente del tipo deserializado desde el índice.

|Datos|Tipo de escáner de archivo|Tipo de resultado de consulta de índice|Tipos relacionados|
|--|--|--|--|
|Referencias|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Símbolos|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> debe usarse en lugar de `IIndexWorkspaceService` para las consultas|
|Valores de datos|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Consultar los datos indizados

Hay dos tipos asincrónicos disponibles para acceder a los datos persistentes. La primera es a través de <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Proporciona acceso básico a un único archivo `FileReferenceResult` y `FileDataResult` datos y lo almacena en caché de resultados. El segundo es el <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> que no usa el almacenamiento en caché, pero permite más capacidades de consulta.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Participa en la indización

Área de trabajo de indexación aproximadamente sigue a la siguiente secuencia:

1. Detección y la persistencia de las entidades del sistema de archivos en el área de trabajo (solo en el análisis inicial de apertura).
1. Por cada archivo, el proveedor que coincida con la prioridad más alta se le pide que busque `FileReferenceInfo`s.
1. Por cada archivo, el proveedor que coincida con la prioridad más alta se le pide que busque `SymbolDefinition`s.
1. Por cada archivo, se le pedirán todos los proveedores `FileDataValue`s.

Las extensiones pueden exportar un escáner implementando `IWorkspaceProviderFactory<IFileScanner>` y exportar el tipo con <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. El `SupportedTypes` argumento de atributo debe ser uno o más valores de <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Para un escáner de ejemplo, consulte el SDK de VS [ejemplo](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> No se exporta un escáner de archivo que admite el `FileScannerTypeConstants.FileScannerContentType` tipo. Se utiliza Microsoft solamente para fines internos.

En situaciones avanzadas, una extensión dinámicamente puede admitir un conjunto arbitrario de tipos de archivo. En lugar de exportar MEF `IWorkspaceProviderFactory<IFileScanner>`, puede exportar una extensión `IWorkspaceProviderFactory<IFileScannerProvider>`. Cuando se inicia la indización, este tipo de generador se importados, creación de instancias y tienen su <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> método invocado. `IFileScanner` las instancias que admiten un valor comprendido entre `FileScannerTpeConstants` se respetan, no solo los símbolos.

## <a name="next-steps"></a>Pasos siguientes

* [Áreas de trabajo y servicios de lenguaje](workspace-language-services.md) -Obtenga información sobre cómo integrar servicios de lenguaje en un área de trabajo de la carpeta abierta.
* [Compilación de área de trabajo](workspace-build.md) -Abrir carpeta es compatible con sistemas como MSBuild y archivos MAKE de compilación.