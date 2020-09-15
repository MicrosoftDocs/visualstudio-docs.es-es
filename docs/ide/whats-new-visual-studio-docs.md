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
ms.openlocfilehash: 4364bd62ac19be958632b8cb2dbbe907013e8a70
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402249"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Documentación de Visual Studio: Novedades de agosto de 2020

Le damos la bienvenida a las novedades de la documentación de Visual Studio de agosto de 2020. En este artículo se enumeran algunos de los cambios más importantes de documentación que se han producido durante este período. Para obtener información sobre las novedades de los meses anteriores, vea el tema del [historial de novedades](whats-new-visual-studio-docs-history.md).

## <a name="azure"></a>Azure

**Artículos nuevos**

- [Incorporación de Azure Application Insights mediante Servicios conectados de Visual Studio](/visualstudio/azure/azure-app-insights-add-connected-service): Servicios conectados de VS 2019 16.7
- [Incorporación de Azure Cache for Redis mediante Servicios conectados de Visual Studio](/visualstudio/azure/azure-cache-for-redis-add-connected-service): Servicios conectados de VS 2019 16.7
- [Incorporación de Azure Cosmos DB a la aplicación mediante Servicios conectados de Visual Studio](/visualstudio/azure/azure-cosmosdb-add-connected-service): Servicios conectados de VS 2019 16.7
- [Incorporación de Azure SignalR mediante Servicios conectados de Visual Studio](/visualstudio/azure/azure-signalr-add-connected-service): Servicios conectados de VS 2019 16.7
- [Incorporación de una conexión a Azure SQL Database](/visualstudio/azure/azure-sql-database-add-connected-service): Servicios conectados de VS 2019 16.7

**Artículos actualizados**

- [Adición de almacenamiento de Azure mediante Servicios conectados de Visual Studio](/visualstudio/azure/vs-azure-tools-connected-services-storage)
  - Servicios conectados de VS 2019 16.7
  - Artículo sobre Servicios conectados de Azure Storage: compatibilidad con la actualización de la interfaz de usuario y los tipos de proyecto

## <a name="code-quality"></a>Calidad del código

**Artículos nuevos**

- [CA1310: Especificar StringComparison para mayor claridad](/visualstudio/code-quality/ca1310); incorporación de documentación de CA1310 y actualización de la documentación de CA1307
- [CA1837: Usar Environment.ProcessId en lugar de Process.GetCurrentProcess().Id](/visualstudio/code-quality/ca1837); documentación de CA1837
- [CA1838: Evitar parámetros `StringBuilder` para P/Invokes](/visualstudio/code-quality/ca1838); incorporación de documentación de CA1838
- [CA2008: No crear tareas sin pasar un elemento TaskScheduler](/visualstudio/code-quality/ca2008); incorporación de documentación de CA2008
- [CA2249: Valorar la posibilidad de usar String.Contains en lugar de String.IndexOf](/visualstudio/code-quality/ca2249); documentación de CA2249
- [CA2361: Asegurarse de que la clase autogenerada que contiene DataSet.ReadXml() no se utilice con datos que no son de confianza](/visualstudio/code-quality/ca2361); más reglas DataSet/DataTable
- [CA2362: Un elemento DataSet o DataTable no seguro en un tipo serializable autogenerado puede ser vulnerable a ataques de ejecución remota de código](/visualstudio/code-quality/ca2362); más reglas DataSet/DataTable
- [IL3000: Evitar usar la ruta de acceso al archivo de ensamblado al publicar como único archivo](/visualstudio/code-quality/il3000); incorporación de documentación de IL3000
- [IL3001: Evitar acceder a la ruta de acceso al archivo de ensamblado al publicar como único archivo](/visualstudio/code-quality/il3001); incorporación de documentación de IL3001

**Updated**

- [CA1002: No exponer listas genéricas](/visualstudio/code-quality/ca1002); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](/visualstudio/code-quality/ca1046); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1307: Especificar StringComparison para mayor claridad](/visualstudio/code-quality/ca1307); incorporación de documentación de CA1310 y actualización de la documentación de CA1307
- [CA1700: No asignar nombre a los valores de enumeración "Reservado"](/visualstudio/code-quality/ca1700); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1707: Los identificadores no deben contener guiones bajos](/visualstudio/code-quality/ca1707); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA1822: Marcar miembros como estáticos](/visualstudio/code-quality/ca1822); incorporación de la sección Capacidad de configuración en la superficie de la API
- [CA2351: Asegurarse de que la entrada de DataSet.ReadXml() sea de confianza](/visualstudio/code-quality/ca2351); más reglas DataSet/DataTable
- [Instalación de analizadores de terceros](/visualstudio/code-quality/install-roslyn-analyzers); estructura y títulos modificados en la documentación sobre el análisis de código

## <a name="containers"></a>Contenedores

**Artículos actualizados**

- [Implementación de un contenedor ASP.NET en un registro de contenedor con Visual Studio](/visualstudio/containers/hosting-web-apps-in-docker): actualizaciones de Herramientas de contenedor en la interfaz de usuario de publicación de Visual Studio 16.7
- [Introducción a Visual Studio Tools para Kubernetes](/visualstudio/containers/tutorial-kubernetes-tools); Tutorial de Kubernetes: incorporación de pasos de eliminación

## <a name="deployment"></a>Implementación

**Artículos nuevos**

- [Extensión de proyectos del Instalador de Visual Studio y .NET Core 3.1](/visualstudio/deployment/installer-projects-net-core): creación de una página de ayuda para las características de .NET Core 3.1 en los proyectos del instalador

**Artículos actualizados**

- [Implementación de la aplicación en una carpeta, IIS, Azure u otro destino](/visualstudio/deployment/deploying-applications-services-and-components-resources): actualizaciones de implementación
- [Implementación en Visual Studio](/visualstudio/deployment/index): actualizaciones de implementación

## <a name="extensibility"></a>Extensibilidad

**Artículos actualizados**
- [Subtipos de proyecto](/visualstudio/extensibility/internals/project-subtypes): corrección de la sangría de los elementos de lista
- [Referencia de valor de color para Visual Studio](/visualstudio/extensibility/ux-guidelines/color-value-reference-for-visual-studio): corrección de AB#1759333 de los encabezados de columna que faltan

## <a name="get-started"></a>Primeros pasos

**Artículos actualizados**

- [Paso 5: Implementación de la aplicación de ASP.NET Core en Azure](/visualstudio/get-started/csharp/tutorial-aspnet-core-ef-step-05): actualizaciones del tutorial en vídeo sobre la nueva interfaz de usuario de Servicios conectados

## <a name="ide"></a>IDE

**Artículos nuevos**

- [Cambio de la tecla de ayuda F1 en Visual Studio](/visualstudio/ide/not-in-toc/change-f1-help-key): refactorización de la página de ayuda F1 predeterminada
- [Ayuda F1 para el editor de texto](/visualstudio/ide/not-in-toc/default-f1-text-editor): refactorización de la página de ayuda F1 predeterminada
- [Conversión de `typeof` en `nameof`](/visualstudio/ide/reference/convert-typeof-to-nameof): conversión de la refactorización de typeof a nameof
- [Simplificación de la expresión LINQ](/visualstudio/ide/reference/simplify-linq-expression): simplificar la refactorización de la expresión LINQ

**Artículos actualizados**

- [Personalizar los diseños de ventana de Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio): adición de información sobre las pestañas de los documentos verticales con moniker en el tema Personalizar los diseños de ventana
- [Cómo notificar un problema con Visual Studio o con el Instalador de Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
  - Se agrega más información a la Identidad administrada del nodo.
  - Se reformula la página completa de Notificar un problema.
- [Ayuda de F1](/visualstudio/ide/not-in-toc/default): refactorizar la página de ayuda de F1 predeterminada
- [Autorrecuperación, Entorno, Opciones (cuadro de diálogo)](/visualstudio/ide/reference/autorecover-environment-options-dialog-box): se incorpora información sobre las ubicaciones de los archivos de autoguardado actualizados
- [Opciones, Editor de texto, Básico (Visual Basic), Avanzado](/visualstudio/ide/reference/options-text-editor-basic-visual-basic): se incorpora documentación básica sobre las sugerencias de nombre de parámetros insertados
- [Opciones, editor de texto, C#, avanzado](/visualstudio/ide/reference/options-text-editor-csharp-advanced): se incorpora documentación básica sobre las sugerencias de nombre de parámetros insertados
- [Sugerencias y trucos de rendimiento de Visual Studio](/visualstudio/ide/visual-studio-performance-tips-and-tricks): se agrega información sobre "Deshabilitar el modo de mapa" y "Deshabilitar el ajuste de línea"
- [Novedades de Visual Studio 2019](/visualstudio/ide/whats-new-visual-studio-2019): actualización de Novedades de Visual Studio 2019 con la información de la disponibilidad general de la versión 16.7

## <a name="rtvs"></a>RTVS

**Artículos actualizados**

- [Trabajar con SQL Server y R](/visualstudio/rtvs/integrating-sql-server-with-r): tablas corregidas para incluir encabezados de columna

## <a name="community-contributors"></a>Colaboradores de la comunidad

Las siguientes personas han contribuido a la documentación de Visual Studio durante este período. Gracias. Para información sobre cómo contribuir a la documentación de Visual Studio, siga las instrucciones que se indican en la [Guía para colaboradores](https://docs.microsoft.com/contribute/).

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