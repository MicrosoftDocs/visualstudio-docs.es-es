---
title: Formato automático en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709978"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>Formato automático en un servicio de lenguaje heredado
Con el formato automático, un servicio de lenguaje inserta automáticamente un fragmento de código cuando un usuario comienza a escribir una construcción de código conocida.

## <a name="automatic-formatting-behavior"></a>Comportamiento de formato automático
 Por ejemplo, al escribir *if*, el servicio de lenguaje inserta automáticamente llaves coincidentes, o si presiona la tecla ENTRAR, el servicio de lenguaje fuerza el punto de inserción de la nueva línea al nivel de sangría adecuado, dependiendo de si la línea anterior abre un nuevo ámbito.

 El filtro de comandos utilizado para el resto del servicio de lenguaje también se puede utilizar para el formato automático. También puede resaltar llaves coincidentes llamando a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>.

## <a name="see-also"></a>Vea también
- [Desarrollar un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
