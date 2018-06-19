---
title: Contexto del proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f52260d63088d7673322f3c42d43d00184a9af
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134700"
---
# <a name="project-context"></a>Contexto del proyecto
Cuando el usuario agrega o trabaja con proyectos y elementos de proyecto, el IDE usa el concepto de contexto del proyecto para determinar cómo varias operaciones deben realizarse.  
  
 Normalmente, los archivos son los objetos de proyecto estándar que el usuario crea explícitamente mediante la selección la **nuevo proyecto** comando o ponen a disposición de seleccionando el **Abrir proyecto** comando el  **Archivo** menú. En estos casos, se crea y se abre en el contexto de un proyecto de archivos y el tipo de proyecto define el contexto de edición del documento.  
  
 Algunos proyectos ofrecen un contexto muy amplio. Por ejemplo, el proyecto administra un espacio de nombres con ámbito de proyecto, mediante programación o conexión de ámbito del proyecto de base de datos para el enlace de datos. El usuario puede abrir con frecuencia los archivos o las conexiones de base de datos directamente mediante un objeto de proyecto determinado, como un elemento de proyecto que se muestra en el Explorador de soluciones.  
  
 En otras ocasiones, el contexto del proyecto de un elemento no se especifica explícitamente. Por ejemplo, el contexto de un elemento no está disponible cuando el usuario abre un archivo seleccionando la **abrir archivo existente** comando el **archivo** menú, cuando el depurador funciona en un archivo, o cuando el usuario hace clic en el **Buscar en archivos** comando en el **buscar y reemplazar** cuadro de diálogo. Para administrar estas situaciones, las llamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> para administrar el proceso de encontrar el proyecto recomendado para abrir un documento.  
  
## <a name="see-also"></a>Vea también  
 [Prioridad del proyecto](../../extensibility/internals/project-priority.md)   
 [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)