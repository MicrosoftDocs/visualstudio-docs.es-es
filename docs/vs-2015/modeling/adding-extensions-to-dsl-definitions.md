---
title: Adding Extensions to DSL Definitions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aeeac82b27b4b5bb71ed05ba658bf9ee048bd85d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292151"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Agregar extensiones a definiciones DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL Definition extension allows you to create a package of extensions to a domain-specific language (DSL). The DSL extension, which is contained in a Visual Studio Integration Extension (VSIX), can be installed on a user's computer in the same manner as a DSL. The additional features can be dynamically enabled and disabled at run time. DSLs do not have to be explicitly designed for extension, and extensions can be designed later or by third parties without altering the extended DSL.

 The additional features can include the following:

- Properties for model and presentation elements

- Decorators for shapes and connectors

- Classes, relationships, shapes and connectors

- Validation constraints

- Toolbox items and tabs

  A user of an extended DSL can create and save a model that contains instances of the additional features, and these can be read by other users who have installed the appropriate extension. Users who have not installed the extension cannot use the additional features, but they can update and save a model without losing the additional features.

  For sample code and more information about this feature, see the [Visual Studio Visualization and Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=186128) Web site.

## <a name="see-also"></a>Vea también
 [Visual Studio Visualization and Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=186128)
