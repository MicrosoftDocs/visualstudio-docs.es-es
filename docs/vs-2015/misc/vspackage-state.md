---
title: Estado de VSPackage | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62980000"
---
# <a name="vspackage-state"></a>Estado de VSPackage
Muchos factores determinan el conjunto de valores persistentes, o el estado, de una [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aplicación.  
  
- Los proyectos tienen propiedades de configuración y de proyecto.  
  
- Las soluciones tienen propiedades.  
  
- La configuración de usuario determina el tamaño y la posición de las ventanas de documento, las ventanas de herramientas, el estado de acoplamiento y los métodos abreviados de teclado.  
  
- Las aplicaciones pueden tener opciones que un usuario establece.  
  
- Los objetos creados por una aplicación pueden tener propiedades propias.  
  
  Estas son algunas de las formas en que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] se puede administrar el estado de una aplicación:  
  
- A través de las páginas de propiedades proyecto y solución.  
  
- Mediante el **Asistente para importar y exportar configuraciones**, que permite a un usuario cambiar la configuración de un equipo a otro.  
  
- Mediante el cuadro de diálogo **Opciones** , que incluye las opciones relacionadas con las aplicaciones.  
  
- A través de la ventana **propiedades** , que expone las propiedades de los objetos.  
  
- A través de la automatización. Una aplicación puede tener acceso al VSPackage y a las propiedades del objeto que se han expuesto a la automatización.  
  
  El estado de la aplicación se basa en varios mecanismos de persistencia que permiten guardar y restaurar el estado de la aplicación.  
  
## <a name="in-this-section"></a>En esta sección  
 [Compatibilidad con la persistencia de estado](../misc/support-for-state-persistence.md)  
 Enumera las estrategias comunes para guardar, restaurar y restablecer el estado de un VSPackage.  
  
 [Opciones y páginas de opciones](../extensibility/internals/options-and-options-pages.md)  
 Presenta las páginas de opciones generales y personalizadas, y explica cómo implementarlas.  
  
 [Creación de una página de opciones](../extensibility/creating-an-options-page.md)  
 Explica cómo crear dos páginas de opciones, una página simple y una página personalizada.  
  
 [Compatibilidad con categorías de configuración](../misc/support-for-settings-categories.md)  
 Describe la configuración del usuario y cómo se crean y se guardan.  
  
 [Creación de una categoría de configuración](../extensibility/creating-a-settings-category.md)  
 Explica cómo crear una [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] categoría de configuración y utilizarla para guardar valores y restaurar valores de un archivo de configuración.  
  
 [Ampliación de propiedades y la ventana de propiedades](../extensibility/extending-properties-and-the-property-window.md)  
 Explica cómo mostrar y cambiar el valor de un objeto en la ventana **propiedades** .  
  
 [Exposición de las propiedades en la ventana de propiedades](../extensibility/exposing-properties-to-the-properties-window.md)  
 Explica cómo exponer las propiedades públicas de un objeto en la ventana **propiedades** .  
  
 [Compatibilidad con las propiedades de proyecto y configuración](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Explica cómo mostrar y cambiar las propiedades de configuración y de proyecto.  
  
 [Obtención de las propiedades del proyecto](../extensibility/getting-project-properties.md)  
 Le guía por los pasos necesarios para crear un VSPackage administrado que muestre las propiedades del proyecto en una ventana de herramientas.  
  
 [Uso del almacén de configuración](../extensibility/using-the-settings-store.md)  
 Explica el mecanismo de persistencia del almacén de configuración y cómo usarlo.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Proporciona una orientación general a los temas que explican cómo crear y usar VSPackages.