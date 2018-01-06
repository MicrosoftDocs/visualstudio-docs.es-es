---
redirect_url: shell/visual-studio-isolated-shell
title: Aislamiento de Visual Studio Shell | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications, isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications, isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a69b93f05619b16657d045cc7ef833d468ae7a51
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-isolated-shell"></a>Aislamiento de Visual Studio Shell
El shell aislado de Visual Studio le permite crear aplicaciones independientes que se pueden ejecutar en paralelo con otras versiones de Visual Studio. Se utiliza principalmente para hospedar herramientas especializadas que se pueden usar los servicios de Visual Studio, pero también tienen un aspecto personalizado y personalización de marca. Características de Visual Studio y los grupos de comandos de menú pueden fácilmente puede activar y desactivar. Títulos de las aplicaciones, los iconos de aplicación y las pantallas de presentación son totalmente personalizables. Para obtener una lista de características personalizables, consulte [personalizar el Shell aislado](../extensibility/customizing-the-isolated-shell.md).  
  
 Para trabajar con un proyecto de shell aislado, debe instalar el SDK de Visual Studio. A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Para crear una aplicación de shell aislado, comience con un proyecto de Visual Studio Shell aislado. Este proyecto contiene todo lo que necesita para desarrollar y probar su propia aplicación de shell aislado. Cuando esté listo para escribir el programa de instalación que implementa la aplicación, debe obtener el paquete redistribuible de shell aislado de [paquete redistribuible de Microsoft Visual Studio Shell (aislado)](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Antes de poder acceder el paquete redistribuible de shell aislado, deberá rellenar una encuesta a clientes breve.  Después de rellenar la encuesta, se le dirigirá a una página de Visual Studio conectar con vínculos de descarga del paquete redistribuible.  Puede encontrar los vínculos de descarga en las visitas al sitio de Visual Studio conectar en la **programas &#124; VISUAL STUDIO 2015 integrado y SHELL aislado** ficha.  
  
> [!NOTE]
>  Para obtener más información sobre cómo implementar una aplicación basada en shell aislada, consulte [Tutorial: crear una aplicación de Shell aislado básica](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Trabajar con el shell aislado  
 Una aplicación de shell aislado de Visual Studio tiene acceso completo a los servicios de Visual Studio y admite la personalización especial y personalización de marca. Hay varias maneras de personalizar una aplicación de shell aislado:  
  
-   Puede utilizar elementos de componente de VSPackages y Managed Extensibility Framework (MEF) para extender una aplicación de shell aislado igual que usaría en cualquier otra extensión de Visual Studio. Para obtener más información, consulte [extender el Shell aislado](../extensibility/extending-the-isolated-shell.md).  
  
-   Para que las características de Visual Studio y los grupos de comandos de menú disponibles o no está disponible, actualice el archivo .vsct en el proyecto de interfaz de usuario de la aplicación.  
  
-   Para quitar **opciones** páginas u otros componentes de shell de Visual Studio desde la aplicación, actualice el archivo .pkgundef de la aplicación.  
  
-   Para modificar otros aspectos de la apariencia o comportamiento del shell, actualice el archivo .pkgdef de la aplicación.  
  
-   Algunos aspectos del shell también pueden especificarse cuando se inicia la aplicación. Para ello, actualice los parámetros en la llamada al punto de entrada de inicio de la appenvstub.dll.  
  
 Para obtener más información acerca de los distintos elementos que se pueden personalizar, consulte [elementos de Shell aislado](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Características estándar del Shell aislado  
 Las siguientes características son estándar para todas las ediciones de Visual Studio.  
  
|Categoría de característica|Característica|  
|----------------------|-------------|  
|Características del IDE|Configuración de importación y exportación<br /><br /> Instalador de controles de cuadro de herramientas<br /><br /> Lista de tareas & lista de errores<br /><br /> Resultados (Ventana)<br /><br /> Página de inicio<br /><br /> Ventana Propiedades<br /><br /> Cuadro de herramientas<br /><br /> Explorador de soluciones<br /><br /> Ventana Marcador<br /><br /> Vista de clases<br /><br /> Examinador de objetos<br /><br /> Ventana Comandos<br /><br /> Esquema del documento<br /><br /> Vista de recursos<br /><br /> Herramienta externa<br /><br /> Windows Communication Foundation (WCF) Agregar referencia de servicio<br /><br /> Language Integrated Query (LINQ) soporte|  
|Diseñador/editor|Código de exploración de herramientas (búsqueda unificada, definición de origen, herencia)<br /><br /> IntelliSense<br /><br /> Etiquetas inteligentes<br /><br /> Administrador de fragmentos de código<br /><br /> Fragmentos de código<br /><br /> Refactorización<br /><br /> Lista descriptiva<br /><br /> Filtrado de IntelliSense<br /><br /> Ventana Definición de código<br /><br /> Diseñador de aplicaciones<br /><br /> Diseñador de Windows Forms<br /><br /> Diseñador de Windows Presentation Foundation (WPF)|  
|Depuración|Evaluador de expresiones de C#<br /><br /> Depuración local<br /><br /> Depuración administrada<br /><br /> Editar y continuar<br /><br /> Depuración entre subprocesos<br /><br /> Visualizaciones<br /><br /> Información sobre datos<br /><br /> Depuración nativa<br /><br /> Depuración de scripts<br /><br /> Depuración de interoperabilidad<br /><br /> Depuración Just-in-time (JIT)<br /><br /> Depurar varios procesos<br /><br /> Depuración de XSLT<br /><br /> Asociar a proceso local<br /><br /> Puntos de seguimiento<br /><br /> Restricciones de punto de interrupción|  
|Datos|Explorador de servidores (simplificado: sólo los datos)<br /><br /> Enlazar datos a datos locales (. MDF o. (MDB)<br /><br /> Enlace de datos al objeto<br /><br /> Enlace de datos al servicio Web<br /><br /> Conjunto completo de controles de datos<br /><br /> Editor XML<br /><br /> Enlazar datos al servidor de base de datos local<br /><br /> Ventana de orígenes de datos|  
|Web|Editor de HTML<br /><br /> Explorador web<br /><br /> Diseñador de formularios Web Forms<br /><br /> Proyecto de sitio Web<br /><br /> Proyecto de aplicación Web|  
|Extensibilidad|Consume componentes MEF y VSPackages|  
  
## <a name="see-also"></a>Vea también  
 [Shell (aislado o integrado)](../extensibility/shell-isolated-or-integrated.md)