---
title: "Decisiones de dise&#241;o del tipo de proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipos de proyecto, la persistencia de archivo de proyecto"
  - "tipos de proyecto, la mecánica de compromiso"
  - "tipos de proyecto, elementos"
  - "tipos de proyecto, las decisiones de diseño"
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Decisiones de dise&#241;o del tipo de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Antes de crear un nuevo tipo de proyecto, debe tomar varias decisiones de diseño atendiendo al tipo de proyecto.  Debe decidir qué tipos de elementos contendrán los proyectos, cómo los archivos de proyecto se conservan, y qué modelo de compromiso utilizará.  
  
## elementos de proyecto  
 ¿El proyecto utilizará los archivos u objetos abstractos?  ¿Si usa archivos, referencia\-serán basadas o archivos basados en directorios?  ¿Los archivos u objetos abstractos van a ser locales o remotos?  
  
 Los elementos de proyecto pueden ser archivos, o pueden ser objetos más abstractos como objetos en un repositorio o conexiones de datos de la base de datos a través de Internet.  Si los elementos son archivos, el proyecto puede ser un proyecto referencia\-basado o basado en directorios.  
  
 En proyectos en referencias, los elementos pueden aparecer en varios proyectos.  Sin embargo, el archivo real que un elemento representa se encuentra en un directorio sólo.  En proyectos basados en directorios, todos los elementos de proyecto existen en la estructura de directorios.  Para obtener más información, vea [NIB:Item Management in Projects](http://msdn.microsoft.com/es-es/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Los elementos locales se almacenan en el mismo equipo donde la aplicación.  Los elementos remotos se pueden almacenar en un servidor independiente en una red local, o en otra parte en internet.  
  
## Persistencia del archivo de proyecto  
 ¿Los datos se almacenan en sistemas comunes de archivo plano, o en almacenamiento estructurado?  ¿Los archivos se abrirán mediante un editor estándar, o un editor específico del proyecto?  
  
 Para conservar sus datos, la mayoría de las aplicaciones guardan los datos en un archivo y, a continuación se leen la reproducción cuando un usuario debe revisar o cambiar la información.  
  
 El almacenamiento estructurado, también denominado archivos compuestos, se utiliza normalmente cuando varios objetos \(COM\) del modelo de objetos componentes deben almacenar los datos almacenados en un único archivo.  Con almacenamiento estructurado, varios componentes de software pueden compartir un único archivo de disco.  
  
 Tiene varias opciones que considerar consulta la persistencia para los elementos del proyecto.  Puede realizar cualquiera de las siguientes opciones:  
  
-   Guarde cada archivo individualmente cuando se ha cambiado.  
  
-   Capturar muchas transacciones en una única operación de **Guardar** .  
  
-   Guarde los archivos localmente, y se publican en un servidor o utilice otro método para guardar elementos de proyecto cuando el elemento representa una conexión de datos a un objeto remoto.  
  
 Para obtener más información sobre la persistencia, vea [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md) y [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## Modelo de memoria asignada del proyecto  
 ¿Los objetos de datos almacenados se abrirán en modo directo o modo de transacción?  
  
 Cuando los objetos de datos se abren en modo directo, los cambios realizados en los datos se incorporan inmediatamente o cuando el usuario guarda manualmente el archivo.  
  
 Cuando los objetos de datos se abren con el modo de transacción, los cambios se guardan en una ubicación temporal en memoria y no se confirman hasta que el usuario elija manualmente para guardar el archivo.  En ese momento, todos los cambios deben aparecer juntos o no sufrirá ningún cambio.  
  
## Vea también  
 [Lista de comprobación: Crear nuevos tipos de proyecto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB:Item Management in Projects](http://msdn.microsoft.com/es-es/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistencia de un proyecto](../../extensibility/internals/project-persistence.md)   
 [Elementos de un modelo de proyecto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Componentes principales de modelo de proyecto](../../extensibility/internals/project-model-core-components.md)   
 [Creación de tipos de proyecto](../../extensibility/internals/creating-project-types.md)