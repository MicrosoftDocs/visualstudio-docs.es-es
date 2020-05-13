---
title: Contexto del proyecto ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51e411f0bca361f96cdffcfd89498908fd21d441
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706594"
---
# <a name="project-context"></a>Contexto del proyecto
Cuando el usuario agrega o trabaja con proyectos y elementos de proyecto, el IDE usa la noción de contexto de proyecto para determinar cómo se deben realizar varias operaciones.

 Normalmente, los archivos son los objetos de proyecto estándar que el usuario crea explícitamente seleccionando el comando **Nuevo proyecto** o pone a disposición seleccionando el comando **Abrir proyecto** en el menú **Archivo.** En estos casos, los archivos se crean y se abren en el contexto de un proyecto y el tipo de proyecto define el contexto para editar el documento.

 Algunos proyectos proporcionan un contexto muy rico. Por ejemplo, el proyecto administra un espacio de nombres de ámbito de proyecto, un espacio de nombres mediante programación o una conexión de base de datos de ámbito de proyecto para el enlace de datos. El usuario puede abrir con frecuencia archivos o conexiones de base de datos directamente mediante un objeto de proyecto determinado, como un elemento de proyecto que se muestra en el Explorador de soluciones.

 En otras ocasiones, el contexto del proyecto de un elemento no se especifica explícitamente. Por ejemplo, el contexto de un elemento no está disponible cuando el usuario abre un archivo seleccionando el comando Abrir archivo **existente** en el menú **Archivo,** cuando el depurador funciona en un archivo o cuando el usuario hace clic en el comando **Buscar en archivos** del cuadro de diálogo Buscar y **reemplazar.** Para controlar estas situaciones, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> el IDE llama para administrar el proceso de búsqueda del mejor proyecto para abrir un documento.

## <a name="see-also"></a>Vea también
- [Prioridad del proyecto](../../extensibility/internals/project-priority.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
