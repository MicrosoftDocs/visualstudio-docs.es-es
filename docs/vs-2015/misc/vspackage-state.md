---
title: Estado de VSPackage | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998868"
---
# <a name="vspackage-state"></a>Estado de VSPackage
Muchos factores determinan el conjunto de valores persistentes o estado, de un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aplicación.  
  
- Los proyectos tienen propiedades de configuración y el proyecto.  
  
- Las soluciones tienen propiedades.  
  
- Configuración de usuario determina el tamaño y posición de las ventanas de documento, las ventanas de herramientas, estado de acoplamiento y métodos abreviados de teclado.  
  
- Las aplicaciones pueden tener las opciones que establece un usuario.  
  
- Los objetos que crea una aplicación pueden tener propiedades propias.  
  
  Estas son algunas de las formas en que un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se puede administrar el estado de la aplicación:  
  
- A través de las páginas de propiedades de proyecto y solución.  
  
- A través de la **importar y exportar configuraciones**, lo que permite que un usuario mover la configuración de un equipo a otro.  
  
- A través de la **opciones** cuadro de diálogo que incluye las opciones relacionadas con las aplicaciones.  
  
- A través de la **propiedades** ventana, que expone las propiedades de objetos.  
  
- Gracias a la automatización. Una aplicación puede tener acceso a propiedades de VSPackage y el objeto que se han expuesto a la automatización.  
  
  Subyacentes a estado de la aplicación se encuentran varios mecanismos de persistencia que permiten guardar y restaurar el estado de la aplicación.  
  
## <a name="in-this-section"></a>En esta sección  
 [Compatibilidad con la persistencia de estado](../misc/support-for-state-persistence.md)  
 Enumera las estrategias comunes para guardar, restaurar y restablecer el estado de un VSPackage.  
  
 [Opciones y páginas de opciones](../extensibility/internals/options-and-options-pages.md)  
 Presenta las páginas de opciones generales y personalizadas y explica cómo implementarlos.  
  
 [Creación de una página de opciones](../extensibility/creating-an-options-page.md)  
 Explica cómo se crean dos páginas de opciones, una página sencilla y una página personalizada.  
  
 [Compatibilidad con categorías de configuración](../misc/support-for-settings-categories.md)  
 Describe la configuración de usuario y cómo se crean y se conservan.  
  
 [Creación de una categoría de configuración](../extensibility/creating-a-settings-category.md)  
 Explica cómo crear un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] categoría de configuración y utilizarlo para guardar los valores para y restaurar los valores de un archivo de configuración.  
  
 [Ampliación de propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)  
 Explica cómo mostrar y cambiar el valor de un objeto en el **propiedades** ventana.  
  
 [Exposición de las propiedades en la ventana de propiedades](../extensibility/exposing-properties-to-the-properties-window.md)  
 Explica cómo exponer las propiedades públicas de un objeto para el **propiedades** ventana.  
  
 [Compatibilidad con las propiedades del proyecto y configuración](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Explica cómo mostrar y cambiar las propiedades de configuración y el proyecto.  
  
 [Obtención de las propiedades del proyecto](../extensibility/getting-project-properties.md)  
 Le guía a través de los pasos necesarios para crear un VSPackage administrado que muestra las propiedades del proyecto en una ventana de herramientas.  
  
 [Uso del almacén de configuración](../extensibility/using-the-settings-store.md)  
 Explica el mecanismo de persistencia de configuración Store y cómo usarlo.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Proporciona una orientación general a temas que explican cómo crear y usar VSPackages.