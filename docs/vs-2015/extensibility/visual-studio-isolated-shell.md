---
title: Shell aislado de Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef2d1cbffab5e38e603b0e50beb896f1c6efa23d
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919203"
---
# <a name="visual-studio-isolated-shell"></a>Shell aislado de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El shell aislado de Visual Studio permite crear aplicaciones independientes que puedan ejecutarse en paralelo con otras versiones de Visual Studio. Se usa principalmente para hospedar herramientas especializadas que pueden usar los servicios de Visual Studio, pero que también tienen una apariencia y una marca personalizadas. Las características de Visual Studio y los grupos de comandos de menú se pueden activar y desactivar fácilmente. Los títulos de las aplicaciones, los iconos de la aplicación y las pantallas de presentación son totalmente personalizables. Para obtener una lista de características personalizables, vea [personalizar el shell aislado](../extensibility/customizing-the-isolated-shell.md).  
  
 Para trabajar con un proyecto de Shell aislado, debe instalar el SDK de Visual Studio. A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Para crear una aplicación de Shell aislado, empiece con un proyecto aislado de Visual Studio Shell. Este proyecto contiene todo lo que necesita para desarrollar y probar su propia aplicación de Shell aislado. Cuando esté listo para escribir el programa de instalación que implementa la aplicación, debe obtener el paquete redistribuible de Shell aislado de [Microsoft Visual Studio Shell (aislado) paquete redistribuible](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/).  
  
> [!NOTE]
> Antes de poder acceder al paquete redistribuible de Shell aislado, se le pedirá que rellene una breve encuesta de clientes.  Después de responder a la encuesta, se le dirigirá a una página de Visual Studio Connect con vínculos de descarga de los paquetes redistribuibles.  Puede encontrar los vínculos de descarga en visitas posteriores al sitio de Visual Studio Connect en la **pestaña &#124; programas integrados y Shell aislado de Visual Studio 2015** .  
  
> [!NOTE]
> Para obtener más información sobre cómo implementar una aplicación basada en Shell aislado, vea [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Trabajar con el shell aislado  
 Una aplicación de Shell aislado de Visual Studio tiene acceso completo a los servicios de Visual Studio y admite personalización y personalización de marca especiales. Hay varias maneras de personalizar una aplicación de Shell aislado:  
  
- Puede usar fragmentos de componentes de VSPackages y Managed Extensibility Framework (MEF) para extender una aplicación de Shell aislado de la misma manera que usaría en cualquier otra extensión de Visual Studio. Para obtener más información, vea [extender el shell aislado](../extensibility/extending-the-isolated-shell.md).  
  
- Para que las características de Visual Studio y los grupos de comandos de menú estén disponibles o no disponibles, actualice el archivo. Vsct en el proyecto de la interfaz de usuario (UI) de la aplicación.  
  
- Para quitar las páginas de **Opciones** u otros componentes de Visual Studio Shell de la aplicación, actualice el archivo. pkgundef de la aplicación.  
  
- Para modificar otros aspectos de la apariencia o el comportamiento del shell, actualice el archivo. pkgdef de la aplicación.  
  
- Algunos aspectos del shell también se pueden especificar cuando se inicia la aplicación. Para ello, actualice los parámetros en la llamada al punto de entrada de inicio de appenvstub. dll.  
  
  Para obtener más información sobre los distintos elementos que se pueden personalizar, vea [elementos del shell aislado](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Características estándar del shell aislado  
 Las siguientes características son estándar para todas las ediciones de Visual Studio.  
  
|Categoría de característica|Característica|  
|----------------------|-------------|  
|Características del IDE|Importación y exportación de configuraciones<br /><br /> Instalador de controles del cuadro de herramientas<br /><br /> Lista de tareas & Lista de errores<br /><br /> Resultados (Ventana)<br /><br /> Página de inicio<br /><br /> Propiedades (ventana)<br /><br /> Cuadro de herramientas<br /><br /> Explorador de soluciones<br /><br /> Marcador (Ventana)<br /><br /> Vista de clases<br /><br /> Explorador de objetos<br /><br /> Ventana Comandos<br /><br /> Esquema del documento<br /><br /> Vista de recursos<br /><br /> Herramienta externa<br /><br /> Windows Communication Foundation (WCF) Agregar referencia de servicio<br /><br /> Compatibilidad con Language Integrated Query (LINQ)|  
|Editor/Diseñador|Herramientas de exploración de código (búsqueda unificada, definición de origen, herencia)<br /><br /> IntelliSense de<br /><br /> SmartTags<br /><br /> Administrador de fragmentos de código<br /><br /> Fragmentos de código de<br /><br /> Refactoring<br /><br /> Lista descriptiva<br /><br /> Filtrado de IntelliSense<br /><br /> Definición de código (Ventana)<br /><br /> Diseñador de aplicaciones<br /><br /> Diseñador de Windows Forms<br /><br /> Diseñador de Windows Presentation Foundation (WPF)|  
|Depuración|C#Evaluador de expresiones<br /><br /> Depuración local<br /><br /> Depuración administrada<br /><br /> Editar y continuar<br /><br /> Depuración entre subprocesos<br /><br /> Visualizaciones<br /><br /> Información sobre datos<br /><br /> Depuración nativa<br /><br /> Depuración de scripts<br /><br /> Depuración de interoperabilidad<br /><br /> Depuración Just-in-Time (JIT)<br /><br /> Depuración de varios procesos<br /><br /> Depuración de XSLT<br /><br /> Asociar al proceso local<br /><br /> Puntos de seguimiento<br /><br /> Restricciones de punto de interrupción|  
|Datos|Explorador de servidores (solo datos simplificados)<br /><br /> Enlazar datos a datos locales (. MDF o. MDB<br /><br /> Enlazar datos a objeto<br /><br /> Enlazar datos al servicio Web<br /><br /> Conjunto completo de controles de datos<br /><br /> Editor XML<br /><br /> Enlazar datos a un servidor de base de datos local<br /><br /> Ventana de orígenes de datos|  
|Web|Editor HTML<br /><br /> Explorador web<br /><br /> Diseñador de formularios Web Forms<br /><br /> Proyecto de sitio web<br /><br /> Proyecto de aplicación Web|  
|Extensibilidad|Consume los componentes VSPackages y MEF|  
  
## <a name="see-also"></a>Vea también  
 [Shell (aislado o integrado)](../extensibility/shell-isolated-or-integrated.md)
