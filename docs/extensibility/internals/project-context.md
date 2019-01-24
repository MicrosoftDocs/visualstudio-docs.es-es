---
title: Contexto del proyecto | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 92a0f875e51b0cb9ff968bf93b8a0877b14149c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990154"
---
# <a name="project-context"></a>Contexto del proyecto
Cuando el usuario agrega o trabaja con proyectos y elementos de proyecto, el IDE usa la noción de contexto del proyecto para determinar cómo varias de las operaciones deben realizarse.  
  
 Normalmente, los archivos son los objetos de proyecto estándar que el usuario crea explícitamente seleccionando el **nuevo proyecto** comando o hace disponible al seleccionar el **Abrir proyecto** comando el  **Archivo** menú. En estos casos, se crean y se abre en el contexto de un proyecto de archivos y el tipo de proyecto define el contexto de edición del documento.  
  
 Algunos proyectos proporcionan un contexto sofisticado. Por ejemplo, el proyecto administra un espacio de nombres con ámbito de proyecto, mediante programación o una conexión de base de datos con ámbito de proyecto para el enlace de datos. Con frecuencia el usuario puede abrir archivos o las conexiones de base de datos directamente mediante el uso de un objeto de proyecto en particular, como un elemento de proyecto que se muestra en el Explorador de soluciones.  
  
 En otras ocasiones, el contexto de un elemento del proyecto no se especifica explícitamente. Por ejemplo, el contexto de un elemento no está disponible cuando el usuario abre un archivo seleccionando la **abra el archivo existente** comando el **archivo** menú cuando el depurador funciona en un archivo, o cuando el usuario hace clic en el **Buscar en archivos** comando en el **buscar y reemplazar** cuadro de diálogo. Para controlar estas situaciones, las llamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> para administrar el proceso de encontrar el proyecto de procedimiento para abrir un documento.  
  
## <a name="see-also"></a>Vea también  
 [Prioridad del proyecto](../../extensibility/internals/project-priority.md)   
 [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)