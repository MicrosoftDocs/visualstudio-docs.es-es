---
title: Magos Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703208"
---
# <a name="wizards"></a>Asistentes
Después de crear un asistente, normalmente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] desea agregarlo al entorno de desarrollo integrado (IDE) para que otros puedan usarlo. A continuación, el asistente agregado aparece en los cuadros de diálogo **Agregar nuevo proyecto** o Agregar nuevo **elemento.** Para ver los cuadros de diálogo Agregar nuevo proyecto o **Agregar nuevo elemento,** haga clic con el botón secundario en una solución abierta en el **Explorador**de soluciones , seleccione **Agregar**y, a continuación, haga clic en **Nuevo proyecto** o **Nuevo elemento**. **Add New Project**

 Los asistentes se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pueden implementar para permitir a los usuarios seleccionar en una vista de árbol de los valores disponibles cuando abren el cuadro de diálogo **Agregar nuevo proyecto** o el cuadro de diálogo Agregar nuevo **elemento,** o cuando hacen clic con el botón derecho en un elemento del Explorador de **soluciones**.

 En el asistente, puede proporcionar la opción de localizar el nombre de un nuevo proyecto o ites, y puede determinar el icono que verán los usuarios cuando seleccionen el asistente. También puede controlar el orden en el que aparecen nuevos elementos en relación con otros elementos disponibles; los elementos no tienen que organizarse alfabéticamente.

 También puede proporcionar un asistente que se inicie de forma diferente, en función de los parámetros personalizados que se pasan al asistente cuando se abre.

 En los temas de esta sección se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] describen los archivos que implementa para que los cuadros de diálogo **Agregar nuevo proyecto** y Agregar nuevo **elemento** muestren el asistente entre los asistentes y plantillas disponibles y los requisitos que debe cumplir el asistente para funcionar correctamente en el IDE.

## <a name="in-this-section"></a>En esta sección
- [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Proporciona información general sobre qué archivos de descripción de directorio de plantilla y explica cómo funcionan en el IDE para mostrar carpetas, archivos .vsz del asistente y archivos de plantilla asociados a un proyecto en los cuadros de diálogo.

- [Archivo de asistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 Explica cómo el IDE inicia los asistentes y enumera las tres partes del archivo .vsz.

- [Interfaz de asistente (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Describe la `IDTWizard` interfaz que los asistentes deben implementar para trabajar en el IDE.

- [Parámetros de contexto](../../extensibility/internals/context-parameters.md)

 Explica cómo se implementan los asistentes y qué ocurre cuando el IDE pasa parámetros de contexto a la implementación.

- [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)

 Explica cómo utilizar parámetros personalizados para controlar el funcionamiento del asistente después de iniciar el asistente.

## <a name="related-sections"></a>Secciones relacionadas
- [Tipos de proyecto](../../extensibility/internals/project-types.md)

 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.

- [Ampliación de proyectos](../../extensibility/extending-projects.md)

 Describe cómo usar los proyectos y soluciones de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para organizar los archivos de código y de recursos, así como la implementación del control de código fuente.
