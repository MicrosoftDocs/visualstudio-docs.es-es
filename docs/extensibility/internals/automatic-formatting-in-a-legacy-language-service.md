---
title: Formato automático en un servicio de lenguaje heredado | Microsoft Docs
description: Obtenga información sobre el formato automático en un servicio de lenguaje heredado, que inserta automáticamente un fragmento de código al empezar a escribir una construcción de código conocida.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a08a56a6820917b3a954c162b1875430875c7585
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086279"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formato automático en un servicio de lenguaje heredado
Con el formato automático, un servicio de lenguaje inserta automáticamente un fragmento de código cuando un usuario comienza a escribir una construcción de código conocida.

## <a name="automatic-formatting-behavior"></a>Comportamiento de formato automático
 Por ejemplo, cuando *se escribe, el servicio de lenguaje* inserta automáticamente llaves coincidentes, o si se presiona la tecla entrar, el servicio de lenguaje fuerza el punto de inserción en la nueva línea al nivel de sangría adecuado, en función de si la línea anterior abre un nuevo ámbito.

 El filtro de comandos que se usa para el resto del servicio de lenguaje también puede usarse para el formato automático. También puede resaltar las llaves coincidentes llamando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .

## <a name="see-also"></a>Consulte también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
