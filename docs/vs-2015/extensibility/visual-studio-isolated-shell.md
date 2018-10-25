---
title: Visual Studio Shell (aislado) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 15d8d4cfb1f3a9067d3fc18933a508ecf60794e4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849052"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Shell (aislado)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El shell aislado de Visual Studio le permite crear aplicaciones independientes que se pueden ejecutar en paralelo con otras versiones de Visual Studio. Se usa principalmente para hospedar herramientas especializadas que se pueden usar los servicios de Visual Studio, pero también tienen un aspecto personalizado y personalización de marca. Características de Visual Studio y los grupos de comandos de menú se pueden fácilmente activar y desactivar. Los títulos de aplicaciones, iconos de aplicación y pantallas de presentación son totalmente personalizables. Para obtener una lista de características personalizables, vea [personalización del Shell aislado](../extensibility/customizing-the-isolated-shell.md).  
  
 Para trabajar con un proyecto de shell aislado, debe instalar el SDK de Visual Studio. A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Para crear una aplicación de shell aislado, comience con un proyecto de Visual Studio Shell aislado. Este proyecto contiene todo lo que necesita para desarrollar y probar su propia aplicación de shell aislado. Cuando esté listo para escribir el programa de instalación que implemente la aplicación, debe obtener el paquete redistribuible de shell aislado de [paquete redistribuible de Microsoft Visual Studio Shell (aislado)](http://go.microsoft.com/fwlink/?LinkId=616022).  
  
> [!NOTE]
>  Para tener acceso el paquete redistribuible de shell aislado, se le pedirá que rellene una breve encuesta de cliente.  Después de completar la encuesta, se le dirigirá a una página de Visual Studio Connect con vínculos de descarga del paquete redistribuible.  Puede encontrar los vínculos de descarga en visitas posteriores al sitio de Visual Studio Connect en el **programas &#124; VISUAL STUDIO 2015 integrado y aislado SHELL** ficha.  
  
> [!NOTE]
>  Para obtener más información sobre cómo implementar una aplicación basada en shell aislada, consulte [Tutorial: crear una aplicación básica de Shell aislado](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="working-with-the-isolated-shell"></a>Trabajar con el shell aislado  
 Una aplicación de shell aislado de Visual Studio tiene acceso completo a los servicios de Visual Studio y admite la personalización de marca y personalización especial. Hay varias maneras de personalizar una aplicación de shell aislado:  
  
- Puede usar componentes de VSPackages y Managed Extensibility Framework (MEF) para ampliar una aplicación de shell aislado igual que usaría en cualquier otra extensión de Visual Studio. Para obtener más información, consulte [ampliación del Shell aislado](../extensibility/extending-the-isolated-shell.md).  
  
- Para que las características de Visual Studio y los grupos de comandos de menú disponibles o no está disponible, actualice el archivo .vsct en el proyecto de interfaz de usuario de la aplicación.  
  
- Para quitar **opciones** páginas u otros componentes de shell de Visual Studio desde la aplicación, actualice el archivo .pkgundef de la aplicación.  
  
- Para modificar otros aspectos de la apariencia o comportamiento del shell, actualice el archivo .pkgdef de la aplicación.  
  
- Algunos aspectos del shell también se pueden especificar cuando se inicia la aplicación. Para ello, actualice los parámetros en la llamada al punto de entrada de inicio de la appenvstub.dll.  
  
  Para obtener más información sobre los distintos elementos que se pueden personalizar, consulte [elementos del Shell aislado](../extensibility/elements-of-the-isolated-shell.md).  
  
## <a name="standard-features-of-the-isolated-shell"></a>Características estándar del Shell aislado  
 Las siguientes características son estándar para todas las ediciones de Visual Studio.  
  
|Categoría de característica|Característica|  
|----------------------|-------------|  
|Características del IDE|Importar/exportar configuraciones<br /><br /> Instalador de controles de cuadro de herramientas<br /><br /> Lista de tareas & lista de errores<br /><br /> Resultados (Ventana)<br /><br /> Página de inicio<br /><br /> Ventana Propiedades<br /><br /> Cuadro de herramientas<br /><br /> Explorador de soluciones<br /><br /> Ventana Marcador<br /><br /> Vista de clases<br /><br /> Examinador de objetos<br /><br /> Ventana Comandos<br /><br /> Esquema del documento<br /><br /> Vista de recursos<br /><br /> Herramienta externa<br /><br /> Windows Communication Foundation (WCF) Agregar referencia de servicio<br /><br /> Compatibilidad con consultas (LINQ) integrada del lenguaje|  
|Diseñador/editor|Exploración de las herramientas (búsqueda unificada, definición de origen, herencia) de código<br /><br /> IntelliSense<br /><br /> Etiquetas inteligentes<br /><br /> Administrador de fragmentos de código<br /><br /> Fragmentos de código<br /><br /> Refactorización<br /><br /> Lista descriptiva<br /><br /> Filtrado de IntelliSense<br /><br /> Ventana Definición de código<br /><br /> Diseñador de aplicaciones<br /><br /> Diseñador de Windows Forms<br /><br /> Diseñador de Windows Presentation Foundation (WPF)|  
|Depuración|Evaluador de expresiones de C#<br /><br /> Depuración local<br /><br /> Depuración administrada<br /><br /> Editar y continuar<br /><br /> Depuración entre subprocesos<br /><br /> Visualizaciones<br /><br /> Información sobre datos<br /><br /> Depuración nativa<br /><br /> Depuración de scripts<br /><br /> Depuración de interoperabilidad<br /><br /> Depuración Just-in-time (JIT)<br /><br /> Depuración de varios procesos<br /><br /> Depuración de XSLT<br /><br /> Asociar al proceso local<br /><br /> Puntos de seguimiento<br /><br /> Restricciones de punto de interrupción|  
|Datos|Explorador de servidores (simplificado - sólo los datos)<br /><br /> Enlazar datos a los datos locales (. MDF o. MDB)<br /><br /> Enlace de datos al objeto<br /><br /> Enlace de datos al servicio Web<br /><br /> Conjunto completo de controles de datos<br /><br /> Editor XML<br /><br /> Enlazar datos al servidor de base de datos local<br /><br /> Ventana de orígenes de datos|  
|Web|Editor de HTML<br /><br /> Explorador web<br /><br /> Diseñador de formularios Web Forms<br /><br /> Proyecto de sitio Web<br /><br /> Proyecto de aplicación Web|  
|Extensibilidad|Consume los componentes MEF y VSPackages|  
  
## <a name="see-also"></a>Vea también  
 [Shell (aislado o integrado)](../extensibility/shell-isolated-or-integrated.md)

