---
title: "Creaci&#243;n de tipos de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipos de proyecto, nuevo"
  - "proyectos [Visual Studio SDK], nuevos tipos de proyecto"
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Creaci&#243;n de tipos de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Puede extender [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mediante la creación de un nuevo tipo de proyecto. Para crear un nuevo tipo de proyecto, debe entender algunos conceptos y realizar una serie de pasos. Los temas siguientes proporcionan información general sobre cómo crear tipos de proyecto.  
  
## En esta sección  
 [Decisiones de diseño del tipo de proyecto](../../extensibility/internals/project-type-design-decisions.md)  
 Describe el elemento, persistencia de archivo de proyecto y las decisiones de diseño mecánico de compromiso que debe realizar antes de crear un nuevo tipo de proyecto.  
  
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Proporciona información general de los pasos que debe seguir para crear un nuevo tipo de proyecto que admite tareas de programación como editar código y compilar, compilar, depurar e implementar aplicaciones en el proyecto.  
  
 [Creación de instancias de proyecto mediante generadores de proyecto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Proporciona información acerca de cómo proporcionar y utilizar un generador de proyecto para crear instancias de un nuevo proyecto.  
  
 [Registra un tipo de proyecto](../../extensibility/internals/registering-a-project-type.md)  
 Proporciona ejemplos de código de las instrucciones del registro que proporcionan rutas de acceso predeterminadas y los datos y una tabla que contienen las entradas de la secuencia de comandos del registro para cada instrucción.  
  
 [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md)  
 Describe el uso de `IPersistFileFormat` para conservar los archivos y objetos no basado en el archivo de proyecto.  
  
 [Uso de MSBuild](../../extensibility/internals/using-msbuild.md)  
 Describe cómo puede utilizar el tipo de proyecto el [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] motor para permitir que los usuarios se crean a partir de compilación [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y en la línea de comandos.  
  
## Secciones relacionadas  
 [Compatibilidad con herramientas de exploración de símbolos](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Explica la arquitectura del código, herramientas de visualización como los **Examinador de objetos** y **la vista de clases** ventana. Describe las interfaces y métodos que se utilizan para implementar la exploración de objetos en un VSPackage.  
  
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Se explica el significado que se reproducen proyectos para determinar el editor que se utiliza cuando se abre un elemento de proyecto y cómo se pueden manipular los recursos del proyecto.  
  
 [Instalación de VSPackages con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Muestra cómo dar el VSPackage su propia identidad única y cómo se ajustan los archivos DLL de VSPackage y otra información en un paquete de Windows Installer \(. Archivo MSI\) para su implementación en los clientes.  
  
 [Jerarquías en Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Describe cómo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] las jerarquías de direcciones y vistas.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Proporciona información general de un paquete VSPackage, un objeto COM instalable que amplía el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno y se explica cómo implementar su propio VSPackage.  
  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Describe cómo utilizar proyectos para modificar código, compilar y generar código, ejecutar y depurar el código y proporciona vínculos a temas detallados sobre cómo crear tipos de proyecto.