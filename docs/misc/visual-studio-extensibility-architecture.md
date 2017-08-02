---
title: "Arquitectura de extensibilidad de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, modelo de entorno"
  - "modelo de entorno, Visual Studio"
ms.assetid: 280fdb55-3e70-41fd-8da0-4039bf5d4894
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# Arquitectura de extensibilidad de Visual Studio
El entorno de desarrollo integrado de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] es un marco para hospedar VSPackages y facilitar la cambiar servicios compartidos.  Un ejemplo de esto es la manera en que el IDE implementa la interfaz de \(UI\) usuario.  El IDE proporciona la ventana contenedora y barras de herramientas y menús predeterminados.  También proporciona una infraestructura COM enriquecida que cree la interfaz de usuario programable.  El comando completo que administra y que distribuye esquema proporciona a los usuarios un marco abierto que proporcione acceso fácil a los conjuntos existentes y instalados del comando.  
  
## arquitectura de la extensibilidad  
 la ilustración siguiente muestra la arquitectura de la extensibilidad de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Observe que el concepto de aplicación de software está ausente.  En su lugar, los componentes de software de los hosts del IDE, denominados VSPackages, que proporcionan funcionalidad de la aplicación.  Esta funcionalidad, a su vez, se comparten en el IDE como servicios.  Servicios de la propuesta de VSPackages que ellos y el otro uso de VSPackages.  El estándar IDE también ofrece una amplia gama de servicios, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, que proporcionan acceso a la funcionalidad de visualización en una ventana del IDE.  
  
 ![Gráfico de arquitectura de entorno](~/extensibility/internals/media/environment.gif "environment")  
vista generalizada de la arquitectura de Visual Studio  
  
 Observe que la relación entre VSPackages y servicios es bidireccional.  Aunque los servicios de uso de VSPackages proporcionados por otros, sino también pueden obtener servicios propios mediante la interfaz de <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> .  Esta arquitectura basado creció fuera de la implementación de Microsoft ActiveX Designer, en la que un servicio es un grupo de interfaces relacionadas que realizan una tarea.  Desde el punto de vista COM estricta, todas las interfaces de un servicio determinado se deben implementar en una única clase COM.  
  
 El IDE estándar obtenga los servicios principales, como <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, y <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>, que son utilizados por VSPackages.  La tabla siguiente muestra y describe algunos de estos servicios.  Para obtener más información, vea [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md).  
  
|servicio de IDE|Descripción|  
|---------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|Proporciona acceso a los servicios del IDE que tratan de funcionalidad básica, de VSPackages, y del registro.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|Proporciona operaciones de una ventana básica y la funcionalidad de Interfaz de usuario\-relacionada en el IDE, como la capacidad de crear las herramientas y las ventanas de documento.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|Proporciona funcionalidad solución\-relacionada básica, como la capacidad de enumerar proyectos, para crear proyectos, y de controlar el proyecto cambia.|  
  
 Debido a su estrecha integración con la interacción de servicios compartidos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE y VSPackages están estrechamente interdependientes.  Sin embargo, a pesar de su interacción próxima tienen distintas responsabilidades.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE es responsable de las tareas siguientes:  
  
-   proporcionar el servicio crítico para uso de VSPackages externo.  
  
-   Proporciona una interfaz programable, que habilita la participación con los elementos de la interfaz de usuario.  
  
-   Creando instancias de VSPackages de acuerdo con de las acciones del usuario o por otro VSPackages solicitante servicios.  
  
-   Proporcionando servicios que hacen posible para la comunicación y la coordinación entre VSPackages.  
  
-   Administrar soluciones y sus archivos necesarios.  
  
-   Proporcionar la administración de ventanas.  
  
-   Proporcionando el enrutamiento y las barras de comandos de comando, como menús, barras de herramientas, y menús contextuales.  
  
-   selección, contexto, y moneda de coordinación.  
  
 VSPackages es responsable de las tareas siguientes:  
  
-   Realizar ciertas rutinas de inicialización y de finalización.  
  
-   Información de escribir en el registro, que usa el IDE para cargar el VSPackages adecuado en los tiempos adecuados.  
  
-   Proporcionando servicios necesarios para comunicarse con el otro VSPackages.  
  
-   Proporcionar las implementaciones para los nuevos tipos de proyecto, editores, y diseñadores.  
  
-   Proporcionando las extensiones para los elementos integrados de la interfaz de usuario, como elementos de tarea, elementos de cuadro de herramientas, y el cuadro de diálogo opciones.  
  
## Vea también  
 [Visual Studio Shell](../extensibility/internals/visual-studio-shell.md)   
 [VSPackages](../extensibility/internals/vspackages.md)   
 [Utilizar y proporcionar servicios](../extensibility/using-and-providing-services.md)   
 [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md)