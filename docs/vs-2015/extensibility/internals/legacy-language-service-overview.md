---
title: Información general del servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6aa3fdcbdb40dca34e17b675478b23d1fd2eef6e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578348"
---
# <a name="legacy-language-service-overview"></a>Información general del servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [información general sobre el servicio de lenguaje heredado](https://docs.microsoft.com/visualstudio/extensibility/internals/legacy-language-service-overview).  
  
Un servicio de lenguaje proporciona compatibilidad con el editor que permite implementar determinados [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] características. Las clases de servicio de lenguaje de Managed Package Framework (MPF) proporcionan compatibilidad completa para las características usadas con frecuencia y compatibilidad parcial con otras características.  
  
## <a name="fully-supported-features-in-the-mpf"></a>Totalmente compatible con características de MPF  
 Las clases de servicio de lenguaje MPF admiten las siguientes características:  
  
-   Resalte de sintaxis  
  
-   esquematizar  
  
-   Comentar bloques de código  
  
-   Coincidencia de llaves  
  
-   Fragmentos de código  
  
-   Propiedades personalizadas del documento  
  
-   Información de parámetros de IntelliSense  
  
-   IntelliSense información rápida  
  
-   Finalizaciones de miembros de IntelliSense  
  
-   Finalización de palabras de IntelliSense  
  
## <a name="partially-supported-features-in-the-mpf"></a>Características admitidas parcialmente en MPF  
 MPF proporciona compatibilidad parcial solo para las siguientes características. Esto significa que debe implementar los métodos que se llaman mediante MPF.  
  
-   Cambiar el formato de código. Proporcione el código que implementa el nuevo formato.  
  
-   Abarca la validación de los puntos de interrupción mediante la identificación de código válido. Proporcione el código que identifica los intervalos de código.  
  
-   Compatibilidad con el depurador **automático** ventana para mostrar las variables. Proporcione el código que determina qué se debe mostrar en la ventana.  
  
-   Compatibilidad con la **barra de navegación** para navegar rápidamente entre los tipos y miembros. Implementar y devolver una clase auxiliar que rellena las listas de la **barra de navegación** cuadros combinados.  
  
## <a name="implementation"></a>Implementación  
 Debe completar varios pasos para implementar el servicio de lenguaje propio y las características del servicio de lenguaje que desee admitir en su idioma. Estos pasos se describen en los temas siguientes:  
  
-   [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
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

