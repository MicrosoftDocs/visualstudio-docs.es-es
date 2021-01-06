---
title: Indexación de áreas de trabajo en Visual Studio | Microsoft Docs
description: Obtenga información sobre la indexación de áreas de trabajo, que es la colección y el almacenamiento persistente de datos para admitir características de IDE enriquecidas para un área de trabajo de carpeta abierta.
ms.custom: SEO-VS-2020
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 6b5c069ce3ae993f2d2371bffae3ac58b286fa70
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877057"
---
# <a name="workspace-indexing"></a>Indexación de áreas de trabajo

En una solución, los sistemas de proyecto son responsables de proporcionar la funcionalidad para compilar, depurar, **Buscar símbolos y** mucho más. Los sistemas de proyectos pueden realizar este trabajo porque entienden la relación y las capacidades de los archivos dentro de un proyecto. Un área de trabajo de [carpeta abierta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) necesita la misma información para proporcionar características de IDE enriquecidas. La recopilación y el almacenamiento persistente de estos datos son un proceso denominado indexación del área de trabajo. Estos datos indexados se pueden consultar a través de un conjunto de API asincrónicas. Los extensores pueden participar en el proceso de indización proporcionando a los <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner> que sabe cómo administrar determinados tipos de archivos.

## <a name="types-of-indexed-data"></a>Tipos de datos indizados

Hay tres tipos de datos que se indizan. Tenga en cuenta que el tipo esperado de los escáneres de archivos difiere del tipo deserializado del índice.

|data|Tipo de escáner de archivos|Tipo de resultado de consulta index|Tipos relacionados|
|--|--|--|--|
|Referencias|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Símbolos|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> debe usarse en lugar de `IIndexWorkspaceService` para las consultas|
|Valores de datos|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Consultar datos indexados

Hay dos tipos asincrónicos disponibles para tener acceso a los datos almacenados. El primero es a través de <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData> . Proporciona acceso básico a los datos y de un solo archivo `FileReferenceResult` `FileDataResult` , y almacena en caché los resultados. La segunda es la <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> que no usa el almacenamiento en caché, pero permite más capacidades de consulta.

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

## <a name="participating-in-indexing"></a>Participar en la indexación

La indexación del área de trabajo sigue la siguiente secuencia:

1. Detección y persistencia de entidades del sistema de archivos en el área de trabajo (solo en el examen inicial de apertura).
1. Por archivo, se pide al proveedor coincidente con la prioridad más alta que busque `FileReferenceInfo` s.
1. Por archivo, se pide al proveedor coincidente con la prioridad más alta que busque `SymbolDefinition` s.
1. Por archivo, se pide a todos los proveedores `FileDataValue` .

Las extensiones pueden exportar un escáner implementando `IWorkspaceProviderFactory<IFileScanner>` y exportando el tipo con <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute> . El `SupportedTypes` argumento de atributo debe ser uno o varios valores de <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants> . Para ver un escáner de ejemplo, vea el [ejemplo](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs)de SDK de vs.

> [!WARNING]
> No exporte un escáner de archivos que admita el `FileScannerTypeConstants.FileScannerContentType` tipo. Solo se usa para fines internos de Microsoft.

En situaciones avanzadas, una extensión puede admitir dinámicamente un conjunto arbitrario de tipos de archivo. En lugar de la exportación de MEF `IWorkspaceProviderFactory<IFileScanner>` , una extensión puede exportar `IWorkspaceProviderFactory<IFileScannerProvider>` . Cuando se inicia la indexación, este tipo de generador se importa, se crea una instancia y se <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> invoca su método. `IFileScanner` se respetarán las instancias que admitan cualquier valor de `FileScannerTpeConstants` , no solo los símbolos.

## <a name="next-steps"></a>Pasos siguientes

* [Áreas de trabajo y servicios de lenguaje](workspace-language-services.md) : Obtenga información sobre cómo integrar los servicios de lenguaje en un área de trabajo de carpeta abierta.
* [Compilación de área de trabajo](workspace-build.md) : la carpeta Open admite sistemas de compilación como MSBuild y archivos make.