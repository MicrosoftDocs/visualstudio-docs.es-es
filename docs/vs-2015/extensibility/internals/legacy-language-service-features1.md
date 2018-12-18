---
title: Features1 del servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb66895066d0af1259c3509c40ec9fa4458e3f79
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774073"
---
# <a name="legacy-language-service-features"></a>Características del servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servicio de lenguaje de paquetes administrados framework (MPF) puede admitir uno o más [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] características, como el resaltado de sintaxis, IntelliSense y validación de punto de interrupción. Cada característica puede implementarse independiente del resto, pero todos requieren un analizador y un escáner excepto resaltado de sintaxis, lo que requiere sólo un escáner.  
  
## <a name="in-this-section"></a>En esta sección  
 [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir la combinación de lenguas coincidentes, también conocido como coincidencia de llaves.  
  
 [Comentario de código en un servicio de lenguaje heredado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir comentar y quitar comentario del código seleccionado.  
  
 [Propiedades de documento personalizado en un servicio de lenguaje heredado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir las propiedades de documento que se incrustan en un archivo de origen.  
  
 [Esquematización en un servicio de lenguaje heredado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir la esquematización a través de la implementación de las regiones ocultas.  
  
 [Cambio de formato de código en un servicio de lenguaje heredado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir el formato de código.  
  
 [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir los fragmentos de código, que son segmentos de código que se insertan y se pueden editar.  
  
 [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Describe lo que es necesario para admitir la operación de IntelliSense información de parámetros para mostrar una firma de método como el método se ha escrito.  
  
 [Información rápida en un servicio de lenguaje heredado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir la operación de información rápida de IntelliSense para mostrar información sobre un identificador.  
  
 [Finalización de miembro en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir la operación de finalización de miembros de IntelliSense para seleccionar a un miembro de un espacio de nombres de una lista.  
  
 [Finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir la operación de palabras completas de IntelliSense para completar las palabras escritas parcialmente.  
  
 [Compatibilidad con la ventana Automático en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Describe qué puede hacer un servicio de lenguaje para admitir la **automático** ventana durante la depuración.  
  
 [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Describe cómo utilizar el **barra de navegación** en la parte superior de la vista del editor para proporcionar navegación rápida a cualquier tipo o miembro en el archivo mostrado en esa vista...  
  
 [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Describe lo que es necesario para admitir el resaltado de sintaxis de código fuente.  
  
 [Validación de puntos de interrupción en un servicio de lenguaje heredado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Describe lo que puede hacer un servicio de lenguaje para admitir puntos de interrupción validación fuera de un depurador.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Describe el analizador y el analizador que son necesarios para implementar todas las características de un servicio de lenguaje que utiliza managed package framework.  
  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Describe lo que es necesario para implementar un servicio de lenguaje mediante MPF.  
  
 [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Describe los pasos necesarios para registrar un servicio de lenguaje basado en MPF con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Usar IntelliSense](../../ide/using-intellisense.md)  
 Explica cómo IntelliSense hace fácil acceder a las referencias del lenguaje.  
  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Proporciona información sobre cómo usar managed package framework (MPF) para implementar un servicio de lenguaje completo en código administrado.

