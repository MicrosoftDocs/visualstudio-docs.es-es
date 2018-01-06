---
title: "Introducción al servicio de lenguaje heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 05805e5cf4b21f4c7d233cab7dd8421ee76f626f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="legacy-language-service-overview"></a>Introducción al servicio de lenguaje heredado
Un servicio de lenguaje proporciona compatibilidad con el editor que le permite implementar determinados [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] características. Las clases de servicio de lenguaje de Managed Package Framework (MPF) proporcionan compatibilidad completa de características usados con frecuencia y compatibilidad parcial para otras características.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Características totalmente compatibles en MPF  
 Las clases de servicio de lenguaje MPF admiten las siguientes características:  
  
-   Resalte de sintaxis  
  
-   esquematizar  
  
-   Bloques de comentarios de código  
  
-   Coincidencia de llaves  
  
-   Fragmentos de código  
  
-   Propiedades de documento personalizadas  
  
-   Información de parámetros de IntelliSense  
  
-   Información rápida de IntelliSense  
  
-   Finalización de miembro de IntelliSense  
  
-   Finalización automática de palabras de IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Características admitidas parcialmente en MPF  
 MPF proporciona compatibilidad parcial solo para las siguientes características. Esto significa que debe implementar los métodos llamados por MPF.  
  
-   Cambiar el formato de código. Proporcionar el código que implementa el nuevo formato.  
  
-   Abarca la validación de los puntos de interrupción mediante la identificación de código válido. Proporcionar el código que identifica los intervalos de código.  
  
-   Compatibilidad con el depurador **automático** ventana para mostrar las variables. Proporcionar el código que determina qué se debe mostrar en la ventana.  
  
-   Compatibilidad con la **barra de navegación** para desplazarse rápidamente entre los tipos y miembros. Implementar y devolver una clase auxiliar que rellena las listas de la **barra de navegación** cuadros combinados.  
  
## <a name="implementation"></a>Implementación  
 Debe completar varios pasos para implementar el propio servicio de lenguaje y las características del servicio de lenguaje que desee admitir en su idioma. En los temas siguientes se describen estos pasos:  
  
-   [Implementar un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Esquematización en un servicio de lenguaje heredado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Comentario de código en un servicio de lenguaje heredado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Cambio de formato de código en un servicio de lenguaje heredado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Propiedades de documento personalizado en un servicio de lenguaje heredado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Finalización de miembro en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Información rápida en un servicio de lenguaje heredado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Compatibilidad con la ventana Automático en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Validación de puntos de interrupción en un servicio de lenguaje heredado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## <a name="see-also"></a>Vea también  
 [Implementar un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)