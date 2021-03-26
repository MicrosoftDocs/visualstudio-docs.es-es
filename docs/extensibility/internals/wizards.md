---
title: Asistentes | Microsoft Docs
description: Obtenga información acerca de cómo mostrar el asistente entre los asistentes y plantillas disponibles en Visual Studio y sobre los requisitos que el asistente debe cumplir en el IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b5c5cb9649689f711844f97e0b57ab23248e9a00
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074163"
---
# <a name="wizards"></a>Asistentes
Después de crear un asistente, normalmente desea agregarlo al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno de desarrollo integrado (IDE) para que otros usuarios puedan usarlo. A continuación, el asistente agregado aparece en los cuadros de diálogo **Agregar nuevo proyecto** o **Agregar nuevo elemento** . Para ver los cuadros de diálogo **Agregar nuevo proyecto** o **Agregar nuevo elemento** , haga clic con el botón secundario en una solución abierta en **Explorador de soluciones**, seleccione **Agregar** y, a continuación, haga clic en **nuevo proyecto** o **nuevo elemento**.

 Los asistentes se pueden implementar en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para permitir a los usuarios seleccionar en una vista de árbol de los valores disponibles cuando abren el cuadro de diálogo **Agregar nuevo proyecto** o el cuadro de diálogo **Agregar nuevo elemento** , o cuando hacen clic con el botón secundario en un elemento de **Explorador de soluciones**.

 En el asistente, puede proporcionar la opción de localizar el nombre de un nuevo proyecto o ITes, y puede determinar el icono que verán los usuarios cuando seleccionen el asistente. También puede controlar el orden en el que aparecen los nuevos elementos en relación con otros elementos disponibles. no es necesario que los elementos estén organizados alfabéticamente.

 También puede proporcionar un asistente que se inicia de manera diferente, en función de los parámetros personalizados que se pasan al asistente cuando se abre.

 En los temas de esta sección se describen los archivos que se implementan para que los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cuadros de diálogo **Agregar nuevo proyecto** y **Agregar nuevo elemento** muestren el asistente entre los asistentes y plantillas disponibles y los requisitos que el asistente debe cumplir para funcionar correctamente en el IDE.

## <a name="in-this-section"></a>En esta sección
- [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Proporciona información general sobre los archivos de Descripción del directorio de plantillas y explica cómo funcionan en el IDE para mostrar carpetas, archivos. vsz y archivos de plantilla asociados a un proyecto en los cuadros de diálogo.

- [Archivo de asistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 Explica cómo el IDE inicia los asistentes y enumera las tres partes del archivo. vsz.

- [Interfaz de asistente (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Describe la `IDTWizard` interfaz que los asistentes deben implementar para trabajar en el IDE.

- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)

 Explica cómo se implementan los asistentes y lo que ocurre cuando el IDE pasa los parámetros de contexto a la implementación.

- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)

 Explica cómo usar los parámetros personalizados para controlar el funcionamiento del asistente después de que se inicie el asistente.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.

- [Ampliación de proyectos](../../extensibility/extending-projects.md)

 Describe cómo usar los proyectos y soluciones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para organizar los archivos de código y de recursos, así como la implementación del control de código fuente.
