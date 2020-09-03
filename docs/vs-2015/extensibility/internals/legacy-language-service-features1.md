---
title: Features1 de servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9506c6756c785741c40f86ae5839101bf0079854
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196126"
---
# <a name="legacy-language-service-features"></a>Características del servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servicio de lenguaje de Managed Package Framework (MPF) puede admitir una o varias [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] características, como el resaltado de sintaxis, IntelliSense y la validación de puntos de interrupción. Cada característica se puede implementar independientemente de las demás, pero todas requieren un analizador y un escáner, excepto el resaltado de sintaxis, que solo requiere un escáner.  
  
## <a name="in-this-section"></a>En esta sección  
 [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir la coincidencia de pares de lenguajes, también conocida como coincidencia de llaves.  
  
 [Comentario de código en un servicio de lenguaje heredado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir los comentarios y quitar comentarios del código seleccionado.  
  
 [Propiedades de documento personalizadas en un servicio de lenguaje heredado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir las propiedades de documento que se incrustan en un archivo de código fuente.  
  
 [Esquematización en un servicio de lenguaje heredado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir la esquematización a través de la implementación de regiones ocultas.  
  
 [Cambio de formato de código en un servicio de lenguaje heredado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir el cambio de formato del código.  
  
 [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir fragmentos de código, que son segmentos de código que se insertan y se pueden editar.  
  
 [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Describe lo que se necesita para admitir la operación de información de parámetros de IntelliSense para mostrar una firma de método a medida que se escribe el método.  
  
 [Información rápida en un servicio de lenguaje heredado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir la operación de información rápida de IntelliSense para mostrar información sobre un identificador.  
  
 [Finalización de miembros en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir la operación de finalización de miembros de IntelliSense para seleccionar un miembro de un espacio de nombres de una lista.  
  
 [Finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir la operación palabra completa de IntelliSense para completar palabras con tipo parcial.  
  
 [Compatibilidad con la ventana Automático en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Describe lo que un servicio de lenguaje puede hacer para admitir la ventana **automático** durante la depuración.  
  
 [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Describe cómo usar la **barra de navegación** en la parte superior de la vista del editor para proporcionar una navegación rápida a cualquier tipo o miembro del archivo mostrado en esa vista.  
  
 [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Describe lo que se necesita para admitir el resaltado de sintaxis del código fuente.  
  
 [Validación de puntos de interrupción en un servicio de lenguaje heredado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Describe lo que un servicio de lenguaje puede hacer para admitir la validación de puntos de interrupción fuera de un depurador.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Describe el analizador y el escáner necesarios para implementar todas las características de un servicio de lenguaje que utiliza el marco de trabajo de paquetes administrados.  
  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Describe lo que se necesita para implementar un servicio de lenguaje mediante MPF.  
  
 [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Describe los pasos necesarios para registrar un servicio de lenguaje basado en MPF con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Usar IntelliSense](../../ide/using-intellisense.md)  
 Explica cómo IntelliSense facilita el acceso a las referencias de lenguaje.  
  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Proporciona información sobre cómo usar Managed Package Framework (MPF) para implementar un servicio de lenguaje completo en código administrado.
