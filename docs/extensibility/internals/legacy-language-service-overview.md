---
title: Descripción general del servicio de idiomas heredados ( Legacy Language Service Overview ) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707354"
---
# <a name="legacy-language-service-overview"></a>Información general del servicio de lenguaje heredado
Un servicio de lenguaje proporciona compatibilidad [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con el editor que le permite implementar ciertas características. Las clases de servicio de lenguaje de Managed Package Framework (MPF) proporcionan compatibilidad completa con las características de uso frecuente y compatibilidad parcial con otras características.

## <a name="fully-supported-features-in-the-mpf"></a>Características totalmente compatibles en el MPF
 Las clases de servicio de lenguaje MPF admiten las siguientes características:

- Resaltado de sintaxis

- esquematizar

- Comentar bloques de código

- Coincidencia de llaves

- Fragmentos de código

- Propiedades personalizadas del documento

- Información de parámetros de IntelliSense

- Información rápida de IntelliSense

- Finalización de miembros de IntelliSense

- Finalización de palabras de IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Características parcialmente admitidas en el MPF
 El MPF solo proporciona compatibilidad parcial con las siguientes características. Esto significa que debe implementar los métodos a los que llama el MPF.

- Reformatear el código. Proporcione el código que implementa el reformateo.

- Validación de puntos de interrupción mediante la identificación de intervalos de código válidos. Proporcione el código que identifica los intervalos de código.

- Compatibilidad con la ventana **Autos** del depurador para mostrar variables. Proporcione el código que determina qué mostrar en la ventana.

- Compatibilidad con la barra de **navegación** para una navegación rápida entre tipos y miembros. Implemente y devuelva una clase auxiliar que rellene las listas en los cuadros combinados Barra de **navegación.**

## <a name="implementation"></a>Implementación
 Debe completar varios pasos para implementar el propio servicio de lenguaje y las características del servicio de lenguaje que desea admitir para su idioma. Estos pasos se describen en los temas siguientes:

- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Esquematización en un servicio de lenguaje heredado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Comentario de código en un servicio de lenguaje heredado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Cambio de formato de código en un servicio de lenguaje heredado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Propiedades de documento personalizadas en un servicio de lenguaje heredado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Finalización de miembros en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Información rápida en un servicio de lenguaje heredado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Compatibilidad con la ventana Automático en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Validación de puntos de interrupción en un servicio de lenguaje heredado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>Vea también
- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Extensibilidad de servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-extensibility.md)
