---
title: "Contexto de proyecto | Microsoft Docs"
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
  - "proyectos [Visual Studio SDK], abrir elementos"
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Contexto de proyecto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cuando el usuario agrega o ejecutar proyectos y elementos de proyecto, el IDE usa el concepto de contexto del proyecto para determinar cómo varias operaciones se deben realizar.  
  
 Normalmente, los archivos son objetos estándar de proyecto que el usuario crea explícitamente seleccionando el comando de **Nuevo proyecto** o crea disponibles seleccionando el comando de **Abrir proyecto** en el menú de **Archivo** .  En estos casos, se crean archivos y abierto en el contexto de un proyecto y el tipo de proyecto define el contexto para modificar el documento.  
  
 Algunos proyectos proporcionan un contexto muy enriquecido.  Por ejemplo, el proyecto administra un proyecto\-scoped, un espacio de nombres de programación o una conexión de base de datos de ámbito de proyecto para el enlace de datos.  El usuario puede archivos con frecuencia abierto o las conexiones a bases de datos utilizando un objeto del proyecto, como un elemento de proyecto mostrado en el explorador de soluciones.  
  
 En otros momentos, el contexto de un elemento no se especifica.  Por ejemplo, el contexto de un elemento no está disponible cuando el usuario abra un archivo seleccionando el comando de **archivo existente abierto** en el menú de **Archivo** , cuando el depurador funciona en un archivo, o cuando el usuario hace clic en el comando de **Buscar en archivos** en el cuadro de diálogo de **Buscar y reemplazar** .  Para controlar estas situaciones, el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> para administrar el proceso de encontrar el mejor proyecto para abrir un documento.  
  
## Vea también  
 [Prioridad del proyecto](../../extensibility/internals/project-priority.md)   
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)