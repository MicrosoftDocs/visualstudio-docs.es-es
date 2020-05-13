---
title: Características del servicio de lenguaje heredado1 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework]
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0be7cb4401792b30eac595faf64162dc375dbb2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707398"
---
# <a name="legacy-language-service-features"></a>Características del servicio de lenguaje heredado
Un servicio de lenguaje de marco de paquetes administrados (MPF) puede admitir una o varias [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] características, como resaltado de sintaxis, IntelliSense y validación de puntos de interrupción. Cada característica se puede implementar independientemente de las demás, pero todas requieren un analizador y un analizador, excepto para el resaltado de sintaxis, que requiere sólo un analizador.

## <a name="in-this-section"></a>En esta sección
- [Coincidencia de llaves en un servicio de lenguaje heredado](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir la coincidencia de pares de idioma, también conocida como coincidencia de llaves.

- [Comentario de código en un servicio de lenguaje heredado](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir comentarios y quitar comentarios del código seleccionado.

- [Propiedades de documento personalizadas en un servicio de lenguaje heredado](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir las propiedades del documento que están incrustadas en un archivo de origen.

- [Esquematización en un servicio de lenguaje heredado](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir la esquematización a través de la implementación de regiones ocultas.

- [Cambio de formato de código en un servicio de lenguaje heredado](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir el reformateo del código.

- [Compatibilidad con fragmentos de código en un servicio de lenguaje heredado](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir fragmentos de código, que son segmentos de código que se insertan y se pueden editar.

- [Información de parámetros en un servicio de lenguaje heredado](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

 Describe lo que se requiere para admitir la operación información de parámetros de IntelliSense para mostrar una firma de método a medida que se escribe el método.

- [Información rápida en un servicio de lenguaje heredado](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir la operación de información rápida de IntelliSense para mostrar información sobre un identificador.

- [Finalización de miembros en un servicio de lenguaje heredado](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir la operación de finalización de miembrode IntelliSense para seleccionar un miembro de un espacio de nombres de una lista.

- [Finalización de palabras en un servicio de lenguaje heredado](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir la operación IntelliSense Complete Word para completar palabras con tipo parcial.

- [Compatibilidad con la ventana Automático en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

 Describe lo que un servicio de lenguaje puede hacer para admitir la ventana **Autos** mientras se está depurando.

- [Compatibilidad con la barra de navegación en un servicio de lenguaje heredado](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

 Describe cómo utilizar la barra de **navegación** en la parte superior de la vista del editor para proporcionar una navegación rápida a cualquier tipo o miembro del archivo que se muestra en esa vista.

- [Coloreado de sintaxis en un servicio de lenguaje heredado](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

 Describe lo que se requiere para admitir el resaltado de sintaxis del código fuente.

- [Validación de puntos de interrupción en un servicio de lenguaje heredado](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

 Describe lo que un servicio de lenguaje puede hacer para admitir la validación de puntos de interrupción fuera de un depurador.

## <a name="related-sections"></a>Secciones relacionadas
- [Escáner y analizador del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Describe el analizador y el analizador necesarios para implementar todas las características de un servicio de lenguaje que usa el marco de paquete administrado.

- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Describe lo que se requiere para implementar un servicio de lenguaje mediante el MPF.

- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Describe los pasos necesarios para registrar un servicio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de lenguaje basado en MPF con .

- [Usar IntelliSense](../../ide/using-intellisense.md)

 Explica cómo IntelliSense facilita el acceso a las referencias de lenguaje.

- [Implementación de un servicio de lenguaje heredado](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Proporciona información sobre cómo usar el marco de paquete administrado (MPF) para implementar un servicio de lenguaje con todas las funciones en código administrado.
