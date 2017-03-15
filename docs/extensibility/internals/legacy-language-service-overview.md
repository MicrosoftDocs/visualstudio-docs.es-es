---
title: "Informaci&#243;n general del servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje [managed package framework], acerca de los servicios de lenguaje"
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Informaci&#243;n general del servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servicio de proporciona compatibilidad de editor que permite implementar determinadas características de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Las clases administradas del \(MPF\) servicio de lenguaje de paquete proporcionan compatibilidad completa para las características con frecuencia\-utilizadas y compatibilidad parcial para otras características.  
  
## Características totalmente compatibles en el MPF  
 Las clases del servicio de lenguaje de MPF admiten las características siguientes:  
  
-   El resaltado de la sintaxis  
  
-   Esquematización  
  
-   bloques de comentario de código  
  
-   El la concordancia de  
  
-   Fragmentos de código  
  
-   Propiedades de documento personalizadas  
  
-   Información de parámetros de IntelliSense  
  
-   información rápida de IntelliSense  
  
-   Finalización de miembros de IntelliSense  
  
-   Finalización de palabras de IntelliSense  
  
## Características parcialmente compatibles en el MPF  
 El MPF sólo proporciona compatibilidad parcial con las características siguientes.  Esto significa que debe implementar los métodos invocados por el MPF.  
  
-   Cambiar el formato del código.  Se proporciona el código que implementa cambiar el formato.  
  
-   Validar los puntos de interrupción identificando los intervalos válidas en el código.  Se proporciona el código que identifica los intervalos de código.  
  
-   Si la ventana de **Automtico** del depurador para mostrar variables.  Se proporciona el código que determina qué mostrar en la ventana.  
  
-   Admitir **Barra de navegación** para la navegación rápida entre los tipos y miembros.  Implementar y devuelve una clase auxiliar que rellene las listas en los cuadros combinados de **Barra de navegación** .  
  
## Implementación  
 Debe finalizar varios pasos para implementar el servicio de lenguaje propio y las características del servicio de lenguaje que desee admitir para el idioma.  Estos pasos se describen en los temas siguientes:  
  
-   [Implementación de un servicio de lenguaje](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrar un servicio de lenguaje](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Esquematización en un servicio de lenguaje heredado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Comentarios de código en un servicio de lenguaje heredado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Cambiar el formato de código en un servicio de lenguaje heredado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Propiedades de documento personalizadas en un servicio de lenguaje heredado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Finalización de miembro en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Información rápida en un servicio de lenguaje heredado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Compatibilidad con la ventana automático en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Validación de puntos de interrupción en un servicio de lenguaje heredado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## Vea también  
 [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)