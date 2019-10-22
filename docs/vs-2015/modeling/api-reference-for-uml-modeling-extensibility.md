---
title: Referencia de API para la extensibilidad del modelado UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending
- UML API
- UML model, API
ms.assetid: 2b2ffe93-c358-4d28-a5e5-3d0474629b58
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e48bf723b8b1cb77cc1f7f4de9cfb562caccde84
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672809"
---
# <a name="api-reference-for-uml-modeling-extensibility"></a>Referencia de la API para la extensibilidad del modelado UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede escribir código de programa para leer y modificar los modelos creados con Visual Studio. La referencia de la API proporciona información sobre las clases específicas para ayudarle con esto. Para obtener más información orientada a tareas, vea los temas de [ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md). Para ver qué versiones de Visual Studio admiten esta característica, vea [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="assemblies"></a>Ensamblados

|Ensamblado|Qué permite hacer|
|--------------|--------------------------------|
|Microsoft.VisualStudio.Uml.Interfaces.dll|-Leer y cambiar elementos del modelo como IUseCase, IAssociation, etc.<br />-Navegar por las relaciones entre elementos.<br /><br /> Los espacios de nombres y tipos se corresponden con los que se definen en la especificación de UML.|
|Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll|-Crear nuevas instancias de elementos de modelo<br />-Obtener acceso y modificar formas y diagramas.|

## <a name="see-also"></a>Vea también
 [Ampliar modelos y diagramas UML](../modeling/extend-uml-models-and-diagrams.md) [referencia de la API para el SDK de modelado para Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
