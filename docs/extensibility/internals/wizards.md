---
title: Asistentes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: af0466ea3c11b75090e45cb9b408ed0723cd8a6f
ms.lasthandoff: 02/22/2017

---
# <a name="wizards"></a>Asistentes
Después de crear un asistente, normalmente desea agregarlo a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integra el entorno de desarrollo (IDE) para que otros puedan utilizarla. A continuación, aparece el Asistente de agregado en la **Agregar nuevo proyecto** o **Agregar nuevo elemento** cuadros de diálogo. Para ver el **Agregar nuevo proyecto** o **Agregar nuevo elemento** diálogo cuadros, haga clic en una solución abierta en **el Explorador de soluciones**, seleccione **agregar**y, a continuación, haga clic en **nuevo proyecto** o **nuevo elemento**.  
  
 Asistentes pueden implementarse en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para permitir que los usuarios select de una vista de árbol de valores disponibles cuando abran el **Agregar nuevo proyecto** cuadro de diálogo o la **Agregar nuevo elemento** cuadro de diálogo, o cuando haga clic en un elemento de **el Explorador de soluciones**.  
  
 En el asistente, puede proporcionar la opción de localizar el nombre de un nuevo proyecto o ITE y puede determinar el icono de que los usuarios verán cuando seleccionen el asistente. También puede controlar el orden en que aparecen los nuevos elementos en relación con otros elementos disponibles; elementos ¿deben organizarse alfabéticamente.  
  
 También puede proporcionar a un asistente que se inicia de forma distinta, basándose en los parámetros personalizados que se pasan al asistente cuando se abre.  
  
 Los temas de esta sección describen los archivos que se implementan para producir el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Agregar nuevo proyecto** y **Agregar nuevo elemento** cuadros de diálogo para mostrar el Asistente entre los asistentes disponibles y las plantillas y los requisitos que debe cumplir el Asistente para que funcione correctamente en el IDE.  
  
## <a name="in-this-section"></a>En esta sección  
 [Descripción del directorio de plantilla (. Archivos VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Proporciona información general de qué plantilla de archivos de descripción de directorio y se explica cómo funcionan en el IDE para mostrar las carpetas, archivos .vsz del asistente y archivos de plantilla que están asociados a un proyecto en los cuadros de diálogo.  
  
 [Asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Explica cómo inicia el IDE de asistentes y enumera las tres partes del archivo .vsz.  
  
 [Interfaz de asistente (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Describe el `IDTWizard` interfaz que deben implementar los asistentes para trabajar en el IDE.  
  
 [Parámetros de contexto](../../extensibility/internals/context-parameters.md)  
 Explica cómo se implementan los asistentes y lo que sucede cuando el IDE pasa los parámetros de contexto para la implementación.  
  
 [Parámetros personalizados](../../extensibility/internals/custom-parameters.md)  
 Explica cómo utilizar parámetros personalizados para controlar el funcionamiento del asistente después de que se inicia el asistente.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Tipos de proyecto](../../extensibility/internals/project-types.md)  
 Proporciona vínculos a temas adicionales que ofrecen información sobre cómo diseñar nuevos tipos de proyecto.  
  
 [Tutorial: Crear un asistente](http://msdn.microsoft.com/Library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Muestra cómo crear a un asistente.  
  
 [Extender proyectos](../../extensibility/extending-projects.md)  
 Describe cómo usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proyectos y soluciones para organizar los archivos de código y archivos de recursos y cómo implementar el control de código fuente.
