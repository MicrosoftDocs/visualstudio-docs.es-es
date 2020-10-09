---
title: 'Documentación de Visual Studio: Historial de novedades '
titleSuffix: ''
description: Historial de novedades en la documentación de Visual Studio
ms.date: 09/30/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: b9aba6b9c4be882498535ab96020461f22722c10
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659308"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Historial de novedades en la documentación de Visual Studio

Le damos la bienvenida al historial de novedades de la documentación de Visual Studio. Este tema contiene los cambios más importantes en la documentación anteriores a agosto de 2020 (a partir de septiembre de 2020). Para ver las últimas novedades, vea [Documentación de Visual Studio: Novedades de la documentación](whats-new-visual-studio-docs.md).

## <a name="august-2020"></a>Agosto de 2020
### <a name="azure"></a>Azure

**Artículos nuevos**

- [Incorporación de Azure Application Insights mediante Servicios conectados de Visual Studio](../azure/azure-app-insights-add-connected-service.md): Servicios conectados de VS 2019 16.7
- [Incorporación de Azure Cache for Redis mediante Servicios conectados de Visual Studio](../azure/azure-cache-for-redis-add-connected-service.md): Servicios conectados de VS 2019 16.7
- [Incorporación de Azure Cosmos DB a la aplicación mediante Servicios conectados de Visual Studio](../azure/azure-cosmosdb-add-connected-service.md): Servicios conectados de VS 2019 16.7
- [Incorporación de Azure SignalR mediante Servicios conectados de Visual Studio](../azure/azure-signalr-add-connected-service.md): Servicios conectados de VS 2019 16.7
- [Incorporación de una conexión a Azure SQL Database](../azure/azure-sql-database-add-connected-service.md): Servicios conectados de VS 2019 16.7

**Artículos actualizados**

- [Adición de almacenamiento de Azure mediante Servicios conectados de Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Servicios conectados de VS 2019 16.7
  - Artículo sobre Servicios conectados de Azure Storage: compatibilidad con la actualización de la interfaz de usuario y los tipos de proyecto

### <a name="code-quality"></a>Calidad del código

**Artículos nuevos**

- [CA1310: Especificar StringComparison para mayor claridad](/dotnet/fundamentals/code-analysis/quality-rules/ca1310); incorporación de documentación de CA1310 y actualización de la documentación de CA1307
- [CA1837: Usar Environment.ProcessId en lugar de Process.GetCurrentProcess().Id](/dotnet/fundamentals/code-analysis/quality-rules/ca1837); documentación de CA1837
- [CA1838: Evitar parámetros `StringBuilder` para P/Invokes](/dotnet/fundamentals/code-analysis/quality-rules/ca1838); incorporación de documentación de CA1838
- [CA2008: No crear tareas sin pasar un elemento TaskScheduler](/dotnet/fundamentals/code-analysis/quality-rules/ca2008); incorporación de documentación de CA2008
- [CA2249: Valorar la posibilidad de usar String.Contains en lugar de String.IndexOf](/dotnet/fundamentals/code-analysis/quality-rules/ca2249); documentación de CA2249
- [CA2361: Asegurarse de que la clase autogenerada que contiene DataSet.ReadXml() no se utilice con datos que no son de confianza](/dotnet/fundamentals/code-analysis/quality-rules/ca2361); más reglas DataSet/DataTable
- [CA2362: Un elemento DataSet o DataTable no seguro en un tipo serializable autogenerado puede ser vulnerable a ataques de ejecución remota de código](/dotnet/fundamentals/code-analysis/quality-rules/ca2362); más reglas DataSet/DataTable
- [IL3000: Evitar usar la ruta de acceso al archivo de ensamblado al publicar como único archivo](/dotnet/fundamentals/code-analysis/quality-rules/il3000); incorporación de documentación de IL3000
- [IL3001: Evitar acceder a la ruta de acceso al archivo de ensamblado al publicar como único archivo](/dotnet/fundamentals/code-analysis/quality-rules/il3001); incorporación de documentación de IL3001

**Updated**

- [CA1002: No exponer listas genéricas](/dotnet/fundamentals/code-analysis/quality-rules/ca1002); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](/dotnet/fundamentals/code-analysis/quality-rules/ca1046); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1307: Especificar StringComparison para mayor claridad](/dotnet/fundamentals/code-analysis/quality-rules/ca1307); incorporación de documentación de CA1310 y actualización de la documentación de CA1307
- [CA1700: No asignar nombre a los valores de enumeración "Reservado"](/dotnet/fundamentals/code-analysis/quality-rules/ca1700); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1707: Los identificadores no deben contener guiones bajos](/dotnet/fundamentals/code-analysis/quality-rules/ca1707); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1822: Marcar miembros como estáticos](/dotnet/fundamentals/code-analysis/quality-rules/ca1822); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA2351: Asegurarse de que la entrada de DataSet.ReadXml() sea de confianza](/dotnet/fundamentals/code-analysis/quality-rules/ca2351); más reglas DataSet/DataTable
- [Instalación de analizadores de terceros](../code-quality/install-roslyn-analyzers.md); estructura y títulos modificados en la documentación sobre el análisis de código

### <a name="containers"></a>Contenedores

**Artículos actualizados**

- [Implementación de un contenedor ASP.NET en un registro de contenedor con Visual Studio](../containers/hosting-web-apps-in-docker.md): actualizaciones de Herramientas de contenedor en la interfaz de usuario de publicación de Visual Studio 16.7
- [Introducción a Visual Studio Tools para Kubernetes](../containers/bridge-to-kubernetes.md); Tutorial de Kubernetes: incorporación de pasos de eliminación

### <a name="deployment"></a>Implementación

**Artículos nuevos**

- [Extensión de proyectos del Instalador de Visual Studio y .NET Core 3.1](../deployment/installer-projects-net-core.md): creación de una página de ayuda para las características de .NET Core 3.1 en los proyectos del instalador

**Artículos actualizados**

- [Implementación de la aplicación en una carpeta, IIS, Azure u otro destino](../deployment/deploying-applications-services-and-components-resources.md): actualizaciones de implementación
- [Implementación en Visual Studio](../deployment/index.yml): actualizaciones de implementación

### <a name="extensibility"></a>Extensibilidad

**Artículos actualizados**
- [Subtipos de proyecto](../extensibility/internals/project-subtypes.md): corrección de la sangría de los elementos de lista
- [Referencia de valor de color para Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md): corrección de AB#1759333 de los encabezados de columna que faltan

### <a name="get-started"></a>Primeros pasos

**Artículos actualizados**

- [Paso 5: Implementación de la aplicación de ASP.NET Core en Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md): actualizaciones del tutorial en vídeo sobre la nueva interfaz de usuario de Servicios conectados

### <a name="ide"></a>IDE

**Artículos nuevos**

- [Cambio de la tecla de ayuda F1 en Visual Studio](./not-in-toc/change-f1-help-key.md): refactorización de la página de ayuda F1 predeterminada
- [Ayuda F1 para el editor de texto](./not-in-toc/default-f1-text-editor.md): refactorización de la página de ayuda F1 predeterminada
- [Conversión de `typeof` en `nameof`](./reference/convert-typeof-to-nameof.md): conversión de la refactorización de typeof a nameof
- [Simplificación de la expresión LINQ](./reference/simplify-linq-expression.md): simplificar la refactorización de la expresión LINQ

**Artículos actualizados**

- [Personalizar los diseños de ventana de Visual Studio](./customizing-window-layouts-in-visual-studio.md): adición de información sobre las pestañas de los documentos verticales con moniker en el tema Personalizar los diseños de ventana
- [Cómo notificar un problema con Visual Studio o con el Instalador de Visual Studio](./how-to-report-a-problem-with-visual-studio.md)
  - Se agrega más información a la Identidad administrada del nodo.
  - Se reformula la página completa de Notificar un problema.
- [Ayuda de F1](./not-in-toc/default.md): refactorizar la página de ayuda de F1 predeterminada
- [Autorrecuperación, Entorno, Opciones (cuadro de diálogo)](./reference/autorecover-environment-options-dialog-box.md): se incorpora información sobre las ubicaciones de los archivos de autoguardado actualizados
- [Opciones, Editor de texto, Básico (Visual Basic), Avanzado](./reference/options-text-editor-basic-visual-basic.md): se incorpora documentación básica sobre las sugerencias de nombre de parámetros insertados
- [Opciones, editor de texto, C#, avanzado](./reference/options-text-editor-csharp-advanced.md): se incorpora documentación básica sobre las sugerencias de nombre de parámetros insertados
- [Sugerencias y trucos de rendimiento de Visual Studio](./visual-studio-performance-tips-and-tricks.md): se agrega información sobre "Deshabilitar el modo de mapa" y "Deshabilitar el ajuste de línea"
- [Novedades de Visual Studio 2019](./whats-new-visual-studio-2019.md): actualización de Novedades de Visual Studio 2019 con la información de la disponibilidad general de la versión 16.7

### <a name="rtvs"></a>RTVS

**Artículos actualizados**

- [Trabajar con SQL Server y R](../rtvs/integrating-sql-server-with-r.md): tablas corregidas para incluir encabezados de columna

## <a name="july-2020"></a>Julio de 2020
### <a name="code-quality"></a>Calidad del código

**Artículos nuevos**

- [CA1417: No usar `OutAttribute` en los parámetros de cadena para P/Invokes](/dotnet/fundamentals/code-analysis/quality-rules/ca1417) - Se agrega documentación para CA1417
- [CA1805: No inicializar innecesariamente](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) - Se agrega documentación para CA1805
- [CA1836: Preferencia de IsEmpty sobre Count si está disponible](/dotnet/fundamentals/code-analysis/quality-rules/ca1836) - Se agrega documentación para CA1836 (Preferencia de IsEmpty sobre Count)
- [CA2016: Reenviar el parámetro CancellationToken a los métodos que lo usan](/dotnet/fundamentals/code-analysis/quality-rules/ca2016) - Documento CA2016: Reenviar el parámetro CancellationToken a los métodos que lo usan
- [CA2350: Asegurarse de que la entrada de DataTable.ReadXml() sea de confianza](/dotnet/fundamentals/code-analysis/quality-rules/ca2350) - Documentos de reglas de deserialización de DataSet/DataTable iniciales
- [CA2351: Asegurarse de que la entrada de DataSet.ReadXml() sea de confianza](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) - Documentos de reglas de deserialización de DataSet/DataTable iniciales
- [CA2352: Un objeto DataSet o DataTable no seguro en un tipo serializable puede ser vulnerable a ataques de ejecución de código remoto](/dotnet/fundamentals/code-analysis/quality-rules/ca2352) - Documentos de reglas de deserialización de DataSet/DataTable iniciales
- [CA2353: Objeto DataSet o DataTable no seguro en un tipo serializable](/dotnet/fundamentals/code-analysis/quality-rules/ca2353) - Documentos de reglas de deserialización de DataSet/DataTable iniciales
- [CA2354: Un objeto DataSet o DataTable no seguro en un gráfico de objetos deserializado puede ser vulnerable a ataques de ejecución de código remoto](/dotnet/fundamentals/code-analysis/quality-rules/ca2354) - Documentos de reglas de deserialización de DataSet/DataTable iniciales
- [CA2355: Objeto DataSet o DataTable no seguro en un gráfico de objetos deserializado](/dotnet/fundamentals/code-analysis/quality-rules/ca2355) - Documentos de reglas de deserialización de DataSet/DataTable iniciales
- [CA2356: Tipo DataTable o DataSet no seguro en un gráfico de objetos deserializado web](/dotnet/fundamentals/code-analysis/quality-rules/ca2356) - Documentos de reglas de deserialización de DataSet/DataTable iniciales

### <a name="containers"></a>Contenedores

**Artículos nuevos**

- [Configuración de Proceso local con Kubernetes](../containers/configure-bridge-to-kubernetes.md) - Proceso local con Kubernetes: configuración de YAML
- [Uso de Proceso local con Kubernetes (versión preliminar)](../containers/bridge-to-kubernetes.md) - Migración de Dev Spaces
- [Funcionamiento de Proceso local con Kubernetes](../containers/overview-bridge-to-kubernetes.md)
  - Proceso local para Kubernetes: Agregar sección de enrutamiento
  - Migración de Dev Spaces

### <a name="cross-platform"></a>Multiplataforma

**Artículos actualizados**

- [Registro de cambios (Visual Studio Tools para Unity, Windows)](../cross-platform/change-log-visual-studio-tools-for-unity.md) - Actualización de la versión del registro de cambios de VSTU a 4.7.1.0
- [Registro de cambios (Visual Studio Tools para Unity, Mac)](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) - Actualización de la versión del registro de cambios de VSTU a 2.7.1.0

### <a name="get-started"></a>Primeros pasos

**Artículos nuevos**

- [Tutorial: Extensión de una aplicación de consola de C# sencilla](../get-started/csharp/tutorial-console-part-2.md) - Publicación de la primera versión del tutorial extendido

### <a name="ide"></a>IDE

**Artículos nuevos**

- [Guía sobre la Comunidad de desarrolladores](./developer-community-guidelines.md) - Se agregó una guía sobre DevCom
- [Finalización de IntelliSense para tipos y métodos de extensión no importados](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Instalar

**Artículos nuevos**

- [Actualización de Visual Studio con un diseño sin conexión mínimo](../install/update-minimal-layout.md) - Característica de diseño mínimo de documento
- [Guía de Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) - Guía de Enterprise

### <a name="javascript"></a>JavaScript

**Artículos nuevos**

- [Compilar código TypeScript (Node.js)](../javascript/compile-typescript-code-npm.md) - Compilación y generación de TypeScript
- [Compilar código TypeScript (ASP.NET°Core)](../javascript/compile-typescript-code-nuget.md) - Compilación y generación de TypeScript

### <a name="msbuild"></a>MSBuild

**Artículos nuevos**

- [Metadatos de elementos MSBuild comunes](../msbuild/common-msbuild-item-metadata.md) - MSBuild: se agrega tabla para metadatos opcionales con Link y LinkBase
- [Filtros de soluciones en MSBuild](../msbuild/solution-filters.md) - Filtros de la solución MSBuild

### <a name="test"></a>Prueba

**Artículos nuevos**

- [Depuración y análisis de pruebas unitarias con el Explorador de pruebas](../test/debug-unit-tests-with-test-explorer.md) - Trabajo de rendimiento del Explorador de pruebas

**Artículos actualizados**

- [Configuración de pruebas unitarias con un archivo *.runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Actualizaciones de la configuración de pruebas unitarias con un archivo runsettings
  - Se cambió la descripción de la opción de Blame y se agregó un ejemplo.