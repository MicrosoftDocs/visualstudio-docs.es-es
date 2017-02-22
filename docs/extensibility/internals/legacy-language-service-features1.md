---
title: "Caracter&#237;sticas del servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje [managed package framework]"
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Caracter&#237;sticas del servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servicio de lenguaje administrado \(MPF\) de paquete puede admitir una o más características de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , como el resaltado de la sintaxis, IntelliSense, y validación de punto de interrupción.  Cada característica puede ser independiente implementado de los otros pero toda requiere un analizador y un escáner salvo el resaltado de sintaxis, que sólo requiere un escáner.  
  
## En esta sección  
 [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Describe qué es necesario para admitir coincidir de pares de lenguas, también conocido como la concordancia de.  
  
 [Comentarios de código en un servicio de lenguaje heredado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Describe qué es necesario para admitir el comentario y uncommenting de código seleccionado.  
  
 [Propiedades de documento personalizadas en un servicio de lenguaje heredado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Describe qué es necesario para admitir las propiedades de documento que se insertan en un archivo de código fuente.  
  
 [Esquematización en un servicio de lenguaje heredado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Describe qué es necesario para admitir la esquematización con la implementación de regiones ocultas.  
  
 [Cambiar el formato de código en un servicio de lenguaje heredado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Describe lo que se requiere para poder modificar el formato del código.  
  
 [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Describe qué es necesario para admitir los fragmentos de código, que son los segmentos de código que se insertan y se pueden editar.  
  
 [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Describe qué es necesario para admitir la operación de la información de parámetros de IntelliSense para mostrar una firma de método mientras se escribe el método.  
  
 [Información rápida en un servicio de lenguaje heredado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Describe qué es necesario para admitir la operación informativa de IntelliSense Quick para mostrar información sobre un identificador.  
  
 [Finalización de miembro en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Describe qué es necesario para admitir la operación de Finalización de IntelliSense para seleccionar un miembro de un espacio de nombres de una lista.  
  
 [Finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Describe qué es necesario para admitir la operación de palabra completa IntelliSense para completar palabras parcialmente escritas.  
  
 [Compatibilidad con la ventana automático en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Describe lo que puede hacer que un servicio de lenguaje para admitir la ventana de **Automtico** durante la depuración.  
  
 [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Describe cómo utilizar **Barra de navegación** a través de la parte superior de la vista del editor para proporcionar navegación rápida a cualquier tipo o miembro en el archivo mostrado en esa vista.  
  
 [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Describe qué es necesario para admitir el resaltado de la sintaxis del código fuente.  
  
 [Validación de puntos de interrupción en un servicio de lenguaje heredado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Describe lo que puede hacer que un servicio de lenguaje para admitir validar los puntos de interrupción fuera de un depurador.  
  
## Secciones relacionadas  
 [Escáneres y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Describe el analizador y el escáner necesarias para implementar todas las características de un servicio de que usa el managed package.  
  
 [Implementación de un servicio de lenguaje](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Describe qué requiere implementar un servicio de mediante el MPF.  
  
 [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Describe los pasos necesarios para registrar un servicio de MPF\-basado con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Utilizar IntelliSense](../../ide/using-intellisense.md)  
 Explica cómo IntelliSense crea el acceso a referencias del lenguaje.  
  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Proporciona información sobre cómo utilizar el \(MPF\) managed package para implementar un servicio de lenguaje completo en código administrado.