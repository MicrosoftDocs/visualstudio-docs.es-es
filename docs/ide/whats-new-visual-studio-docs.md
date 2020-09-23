---
title: 'Documentación de Visual Studio: Novedades de agosto de 2020 '
titleSuffix: ''
description: Novedades de la documentación de Visual Studio de agosto de 2020
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 2411299fbab6dfba8ced0f689bd33825b62614af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808986"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Documentación de Visual Studio: Novedades de agosto de 2020

Le damos la bienvenida a las novedades de la documentación de Visual Studio de agosto de 2020. En este artículo se enumeran algunos de los cambios más importantes de documentación que se han producido durante este período. Para obtener información sobre las novedades de los meses anteriores, vea el tema del [historial de novedades](whats-new-visual-studio-docs-history.md).

## <a name="azure"></a>Azure

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

## <a name="code-quality"></a>Calidad del código

**Artículos nuevos**

- [CA1310: Especificar StringComparison para mayor claridad](../code-quality/ca1310.md); incorporación de documentación de CA1310 y actualización de la documentación de CA1307
- [CA1837: Usar Environment.ProcessId en lugar de Process.GetCurrentProcess().Id](../code-quality/ca1837.md); documentación de CA1837
- [CA1838: Evitar parámetros `StringBuilder` para P/Invokes](../code-quality/ca1838.md); incorporación de documentación de CA1838
- [CA2008: No crear tareas sin pasar un elemento TaskScheduler](../code-quality/ca2008.md); incorporación de documentación de CA2008
- [CA2249: Valorar la posibilidad de usar String.Contains en lugar de String.IndexOf](../code-quality/ca2249.md); documentación de CA2249
- [CA2361: Asegurarse de que la clase autogenerada que contiene DataSet.ReadXml() no se utilice con datos que no son de confianza](../code-quality/ca2361.md); más reglas DataSet/DataTable
- [CA2362: Un elemento DataSet o DataTable no seguro en un tipo serializable autogenerado puede ser vulnerable a ataques de ejecución remota de código](../code-quality/ca2362.md); más reglas DataSet/DataTable
- [IL3000: Evitar usar la ruta de acceso al archivo de ensamblado al publicar como único archivo](../code-quality/il3000.md); incorporación de documentación de IL3000
- [IL3001: Evitar acceder a la ruta de acceso al archivo de ensamblado al publicar como único archivo](../code-quality/il3001.md); incorporación de documentación de IL3001

**Updated**

- [CA1002: No exponer listas genéricas](../code-quality/ca1002.md); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046.md); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1307: Especificar StringComparison para mayor claridad](../code-quality/ca1307.md); incorporación de documentación de CA1310 y actualización de la documentación de CA1307
- [CA1700: No asignar nombre a los valores de enumeración "Reservado"](../code-quality/ca1700.md); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1707: Los identificadores no deben contener guiones bajos](../code-quality/ca1707.md); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1822: Marcar miembros como estáticos](../code-quality/ca1822.md); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA2351: Asegurarse de que la entrada de DataSet.ReadXml() sea de confianza](../code-quality/ca2351.md); más reglas DataSet/DataTable
- [Instalación de analizadores de terceros](../code-quality/install-roslyn-analyzers.md); estructura y títulos modificados en la documentación sobre el análisis de código

## <a name="containers"></a>Contenedores

**Artículos actualizados**

- [Implementación de un contenedor ASP.NET en un registro de contenedor con Visual Studio](../containers/hosting-web-apps-in-docker.md): actualizaciones de Herramientas de contenedor en la interfaz de usuario de publicación de Visual Studio 16.7
- [Introducción a Visual Studio Tools para Kubernetes](../containers/tutorial-kubernetes-tools.md); Tutorial de Kubernetes: incorporación de pasos de eliminación

## <a name="deployment"></a>Implementación

**Artículos nuevos**

- [Extensión de proyectos del Instalador de Visual Studio y .NET Core 3.1](../deployment/installer-projects-net-core.md): creación de una página de ayuda para las características de .NET Core 3.1 en los proyectos del instalador

**Artículos actualizados**

- [Implementación de la aplicación en una carpeta, IIS, Azure u otro destino](../deployment/deploying-applications-services-and-components-resources.md): actualizaciones de implementación
- [Implementación en Visual Studio](../deployment/index.yml): actualizaciones de implementación

## <a name="extensibility"></a>Extensibilidad

**Artículos actualizados**
- [Subtipos de proyecto](../extensibility/internals/project-subtypes.md): corrección de la sangría de los elementos de lista
- [Referencia de valor de color para Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md): corrección de AB#1759333 de los encabezados de columna que faltan

## <a name="get-started"></a>Primeros pasos

**Artículos actualizados**

- [Paso 5: Implementación de la aplicación de ASP.NET Core en Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md): actualizaciones del tutorial en vídeo sobre la nueva interfaz de usuario de Servicios conectados

## <a name="ide"></a>IDE

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

## <a name="rtvs"></a>RTVS

**Artículos actualizados**

- [Trabajar con SQL Server y R](../rtvs/integrating-sql-server-with-r.md): tablas corregidas para incluir encabezados de columna

## <a name="community-contributors"></a>Colaboradores de la comunidad

Las siguientes personas han contribuido a la documentación de Visual Studio durante este período. Gracias. Para información sobre cómo contribuir a la documentación de Visual Studio, siga las instrucciones que se indican en la [Guía para colaboradores](/contribute/).

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG): Alex Black (11)
- [Youssef1313](https://github.com/Youssef1313): Youssef Victor (8)
- [hyoshioka0128](https://github.com/hyoshioka0128): Hiroshi Yoshioka (3)
- [AstroChoco](https://github.com/AstroChoco): Qian Lu (Chocolate) (1)
- [athyunnath](https://github.com/athyunnath): Athyunnath Eleti (1)
- [caro-oviedo](https://github.com/caro-oviedo): Caro Oviedo (1)
- [Evangelink](https://github.com/Evangelink): Amaury Levé (1)
- [jethas-bennettjones](https://github.com/jethas-bennettjones): Shafiq Jetha (1)
- [nebuk89](https://github.com/nebuk89): Ben De St Paer-Gotch (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov): Petr Kulikov (1)
- [riQQ](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger): Timo Cornelius Metzger (1)
- [weitzhandler](https://github.com/weitzhandler): Shimmy (1)