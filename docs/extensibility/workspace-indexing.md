---
title: Área de trabajo de indización en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 9bf3a094184e2d57b4a066234d84a6ab6380510b
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="workspace-indexing"></a>Indización de área de trabajo

En una solución, los sistemas del proyecto son responsables de proporcionar funcionalidad de compilación, depuración, **GoTo** buscar símbolos y mucho más. Sistemas del proyecto pueden realizar este trabajo ya entienden la relación y las capacidades de archivos dentro de un proyecto. Un [Abrir carpeta](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) área de trabajo tiene la misma información para proporcionar características enriquecidas IDE también. La recopilación y el almacenamiento persistente de los datos es un proceso denominado indización de área de trabajo. Estos datos indizados se pueden consultar a través de un conjunto de API asíncronas. Extender puede participar en el proceso de indización proporcionando <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>s que sabe cómo administrar determinados tipos de archivos.

## <a name="types-of-indexed-data"></a>Tipos de datos indizados

Hay tres tipos de datos que se indizan. Tenga en cuenta el tipo esperado de escáneres de archivo difiere del tipo de deserializar en el índice.

|Datos|Tipo de escáner de archivo|Tipo de resultado de consulta de índice|Tipos relacionados|
|--|--|--|--|
|Referencias|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Símbolos|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> debe usarse en lugar de `IIndexWorkspaceService` para las consultas|
|Valores de datos|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Consultar los datos indizados

Hay dos tipos asincrónicos disponibles para tener acceso a los datos almacenados. La primera es a través de <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Proporciona el acceso básico a un único archivo `FileReferenceResult` y `FileDataResult` datos y lo almacena en caché los resultados. El segundo es el <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> que no usa el almacenamiento en caché, pero permite más capacidades de consultas.

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

Indización de área de trabajo sigue aproximadamente a la siguiente secuencia:

1. Detección y persistencia de las entidades del sistema de archivos en el área de trabajo (solo en el examen de apertura inicial).
1. Por cada archivo, el proveedor de búsqueda de coincidencias con la prioridad más alta se le pide que busque `FileReferenceInfo`s.
1. Por cada archivo, el proveedor de búsqueda de coincidencias con la prioridad más alta se le pide que busque `SymbolDefinition`s.
1. Por cada archivo, todos los proveedores se piden `FileDataValue`s.

Extensiones pueden exportar un escáner implementando `IWorkspaceProviderFactory<IFileScanner>` y exportar el tipo con <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. El `SupportedTypes` argumento de atributo debe ser uno o más valores de <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Para un escáner de ejemplo, vea el SDK de VS [ejemplo](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> No se exporta un escáner de archivo que admite el `FileScannerTypeConstants.FileScannerContentType` tipo. Se utiliza para fines internos de Microsoft, solo.

En situaciones avanzadas, una extensión dinámicamente podría admitir un conjunto arbitrario de tipos de archivo. En lugar de exportar MEF `IWorkspaceProviderFactory<IFileScanner>`, puede exportar una extensión `IWorkspaceProviderFactory<IFileScannerProvider>`. Cuando se inicia la indización, este tipo de generador se pueden importar, crea una instancia y tienen su <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> método invocado. `IFileScanner` instancias de compatibilidad con cualquier valor de `FileScannerTpeConstants` se aplican, no solo los símbolos.

## <a name="next-steps"></a>Pasos siguientes

* [Áreas de trabajo y servicios de lenguaje](workspace-language-services.md) -obtener información sobre cómo integrar servicios de lenguaje en un área de trabajo de la carpeta abierta.
* [Compilación de área de trabajo](workspace-build.md) -Abrir carpeta admite crear sistemas como MSBuild y MAKE (archivos).