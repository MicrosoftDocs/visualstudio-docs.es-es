---
title: Contexto de proyecto | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio IDE usa el contexto del proyecto para determinar cómo realizar operaciones cuando el usuario agrega o trabaja con proyectos y elementos de proyecto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 73e3c8a94607e7e0b31bacddac8e7f19b6139328
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899828"
---
# <a name="project-context"></a>Contexto del proyecto
Cuando el usuario agrega o trabaja con proyectos y elementos de proyecto, el IDE usa la noción de contexto del proyecto para determinar cómo se deben realizar varias operaciones.

 Normalmente, los archivos son los objetos de proyecto estándar  que el usuario crea explícitamente seleccionando el comando Nuevo proyecto o pone a disposición seleccionando el comando Abrir proyecto en el **menú** Archivo.  En estos casos, los archivos se crean y abren en el contexto de un proyecto y el tipo de proyecto define el contexto para editar el documento.

 Algunos proyectos proporcionan un contexto muy enriquecido. Por ejemplo, el proyecto administra una conexión de base de datos de ámbito de proyecto o de ámbito de proyecto para el enlace de datos. Con frecuencia, el usuario puede abrir archivos o conexiones de base de datos directamente mediante un objeto de proyecto determinado, como un elemento de proyecto que se muestra en Explorador de soluciones.

 En otras ocasiones, el contexto de proyecto de un elemento no se especifica explícitamente. Por ejemplo, el contexto de un elemento no está disponible  cuando el usuario  abre un archivo seleccionando el comando Abrir archivo existente en el menú  Archivo, cuando el depurador funciona en un archivo o cuando el usuario hace clic en el comando Buscar en archivos en el cuadro de diálogo Buscar y reemplazar.  Para controlar estas situaciones, el IDE llama a para administrar el proceso de búsqueda del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> mejor proyecto para abrir un documento.

## <a name="see-also"></a>Consulta también
- [Prioridad del proyecto](../../extensibility/internals/project-priority.md)
- [Adición de plantillas de proyecto y de elementos de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
