---
title: Asistentes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03cee9de14da76ea65882d906acb3af88e72e999
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="wizards"></a>Asistentes
Después de crear un asistente, normalmente desea agregarlo a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrar el entorno de desarrollo (IDE) de modo que otros puedan utilizarla. A continuación, aparece el Asistente de agregado en la **Agregar nuevo proyecto** o **Agregar nuevo elemento** cuadros de diálogo. Para ver el **Agregar nuevo proyecto** o **Agregar nuevo elemento** diálogo cuadros, haga clic en una solución abierta en **el Explorador de soluciones**, seleccione **agregar**, y a continuación, haga clic en **nuevo proyecto** o **nuevo elemento**.  
  
 Asistentes pueden implementarse de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para permitir que los usuarios select en una vista de árbol de valores disponibles cuando abran el **Agregar nuevo proyecto** cuadro de diálogo o la **Agregar nuevo elemento** cuadro de diálogo, o cuando haga clic en un elemento de **el Explorador de soluciones**.  
  
 En el asistente, puede proporcionar la opción de localizar el nombre de un proyecto nuevo o ites y puede determinar el icono de que los usuarios verán cuando seleccionen el asistente. También puede controlar el orden en que los nuevos elementos aparecen con respecto a otros elementos disponibles; no es necesario que los elementos se ordenan alfabéticamente.  
  
 También puede proporcionar a un asistente que se inicia de forma diferente, según los parámetros personalizados que se pasan al asistente cuando se abre.  
  
 Los temas de esta sección describen los archivos que se implementan para que se produzca la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Agregar nuevo proyecto** y **Agregar nuevo elemento** cuadros de diálogo para mostrar el Asistente entre las plantillas y los asistentes disponibles y los requisitos que el asistente debe cumplir para que funcione correctamente en el IDE.  
  
## <a name="in-this-section"></a>En esta sección  
 [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Proporciona información general de qué plantilla de archivos de descripción de directorio y se explica cómo funcionan en el IDE para mostrar las carpetas, archivos .vsz del asistente y archivos de plantilla que están asociados a un proyecto en los cuadros de diálogo.  
  
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Explica cómo inicia el IDE de asistentes y enumera las tres partes del archivo .vsz.  
  
 [Interfaz de asistente (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Describe el `IDTWizard` interfaz que deben implementar los asistentes para trabajar en el IDE.  
  
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)  
 Explica cómo se implementan los asistentes y lo que ocurre cuando el IDE pasa parámetros de contexto a la implementación.  
  
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)  
 Explica cómo utilizar parámetros personalizados para controlar el funcionamiento del Asistente una vez que se inicia el asistente.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.  
  
 [Ampliación de proyectos](../../extensibility/extending-projects.md)  
 Describe cómo usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos y soluciones para organizar los archivos de código y archivos de recursos y cómo implementar el control de código fuente.