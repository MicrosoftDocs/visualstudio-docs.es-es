---
title: Configuración de la solución ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705374"
---
# <a name="solution-configuration"></a>Configuración de soluciones
Las configuraciones de solución almacenan propiedades de nivel de solución. Dirigen el comportamiento de la tecla **Inicio** (F5) y los comandos **Decompilar.** De forma predeterminada, estos comandos compilan e inician la configuración de depuración. Ambos comandos se ejecutan en el contexto de una configuración de solución. Esto significa que el usuario puede esperar que F5 inicie y compile cualquier solución activa que se configure a través de la configuración. El entorno está diseñado para optimizar las soluciones en lugar de los proyectos cuando se trata de construir y ejecutar.

 La barra de herramientas estándar de Visual Studio contiene un botón Inicio y una lista desplegable de configuración de la solución a la derecha del botón Inicio. Esta lista permite a los usuarios elegir la configuración que se iniciará cuando se presiona F5, crear sus propias configuraciones de solución o editar una configuración existente.

> [!NOTE]
> No hay interfaces de extensibilidad para crear o editar las configuraciones de la solución. Se debe usar `DTE.SolutionBuild`. Sin embargo, hay API de extensibilidad para administrar la compilación de la solución. Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>.

 A continuación se muestra cómo implementar las configuraciones de solución admitidas por el tipo de proyecto:

- proyecto

   Muestra los nombres de los proyectos que se encuentran en la solución actual.

- Configuración

   Para proporcionar la lista de configuraciones admitidas por el tipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>de proyecto y que se muestran en las páginas de propiedades, implemente .

   La columna Configuración muestra el nombre de la configuración del proyecto que se va a compilar en esta configuración de la solución y enumera todas las configuraciones del proyecto al hacer clic en el botón de flecha. El entorno <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> llama al método para rellenar esta lista. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> el método indica que el proyecto admite la edición de configuración, las selecciones Nuevo o Editar también se muestran en el encabezado Configuración. Cada una de estas selecciones inicia `IVsCfgProvider2` cuadros de diálogo que llaman a métodos de la interfaz para editar las configuraciones del proyecto.

   Si un proyecto no admite configuraciones, la columna Configuración muestra Ninguno y está deshabilitada.

- Plataforma

   Muestra la plataforma para la que se compila la configuración del proyecto seleccionado y enumera todas las plataformas disponibles para el proyecto al hacer clic en el botón de flecha. El entorno <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> llama al método para rellenar esta lista. Si <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> el método indica que el proyecto admite la edición de plataformas, las selecciones Nuevo o Editar también se muestran en el encabezado Plataforma. Cada una de estas selecciones `IVsCfgProvider2` inicia cuadros de diálogo que llaman a métodos para editar las plataformas disponibles del proyecto.

   Si un proyecto no admite plataformas, la columna de plataforma de ese proyecto muestra Ninguno y está deshabilitada.

- Compilar

   Especifica si el proyecto se compila o no mediante la configuración de la solución actual. Los proyectos no seleccionados no se compilan cuando se invocan los comandos de compilación de nivel de solución a pesar de las dependencias de proyecto que contienen. Los proyectos no seleccionados para compilarse todavía se incluyen en la depuración, ejecución, empaquetado e implementación de la solución.

- Implementación

   Especifica si el proyecto se implementará o no cuando se usen los comandos Inicio o Implementación con la configuración de compilación de la solución seleccionada. La casilla de verificación de este campo estará disponible <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> si <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> el proyecto admite la implementación mediante la implementación de la interfaz en su objeto.

  Una vez que se agrega una nueva configuración de solución, el usuario puede seleccionarla en el cuadro de lista desplegable Configuración de la solución de la barra de herramientas estándar para compilar o iniciar esa configuración.

## <a name="see-also"></a>Vea también
- [Administración de opciones de configuración](../../extensibility/internals/managing-configuration-options.md)
- [Configuración del proyecto para la compilación](../../extensibility/internals/project-configuration-for-building.md)
- [Objeto de configuración del proyecto](../../extensibility/internals/project-configuration-object.md)
