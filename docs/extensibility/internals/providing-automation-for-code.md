---
title: Proporcionar automatización para código | Microsoft Docs
description: Obtenga información sobre la implementación de un modelo de código, que requiere la implementación de interfaces determinadas por la estructura de datos interna.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 57d5337ae088560bb94a6af39902e90b6af02686
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060970"
---
# <a name="providing-automation-for-code"></a>Provisión de automatización para código
No es necesario crear un modelo de automatización para el código. El SDK de entorno no proporciona un ejemplo para hacerlo. Para obtener información sobre los modelos de código, vea el <xref:EnvDTE.CodeModel> objeto.

 Para implementar un modelo de código, debe implementar las interfaces determinadas por la estructura de datos interna. Los objetos se deben derivar de la `IDispatch` clase.

 Los objetos que extiende, <xref:EnvDTE.CodeModel> y <xref:EnvDTE.FileCodeModel> , están disponibles en el <xref:EnvDTE.Project> objeto y tienen un aspecto similar al siguiente:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Puede optar por implementar únicamente la `CodeModel` interfaz o `FileCodeModel` en el objeto que devuelve de los `Project` objetos y <xref:EnvDTE.ProjectItem> . Proporcione cualquier funcionalidad de esta interfaz que sea adecuada para el sistema del proyecto.

 Si desea agregar características, como métodos o propiedades, que no están disponibles desde las `CodeModel` interfaces estándar y `FileCodeModel` , cree su propia interfaz que herede de la norma. Asegúrese de documentarlo con el sistema del proyecto para que los usuarios finales sepan buscarlo. Se devuelve la interfaz estándar, pero el usuario puede llamar al `QueryInterface` método o convertir a la interfaz si se sabe que existe.

## <a name="see-also"></a>Consulte también
- [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)
