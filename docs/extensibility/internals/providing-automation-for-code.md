---
title: Proporcionar automatización para código | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 874446aa6bf2e40a120aac49e7d91fd3d861d1d4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724961"
---
# <a name="providing-automation-for-code"></a>Provisión de automatización para código
No es necesario crear un modelo de automatización para el código. El SDK de entorno no proporciona un ejemplo para hacerlo. Para obtener información sobre los modelos de código, vea el objeto <xref:EnvDTE.CodeModel>.

 Para implementar un modelo de código, debe implementar las interfaces determinadas por la estructura de datos interna. Los objetos se deben derivar de la clase `IDispatch`.

 Los objetos que extiende, <xref:EnvDTE.CodeModel> y <xref:EnvDTE.FileCodeModel>, están disponibles en el objeto <xref:EnvDTE.Project> y tienen un aspecto similar al siguiente:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Puede optar por implementar solo el `CodeModel` o la interfaz de `FileCodeModel` en el objeto que se devuelve de los objetos `Project` y <xref:EnvDTE.ProjectItem>. Proporcione cualquier funcionalidad de esta interfaz que sea adecuada para el sistema del proyecto.

 Si desea agregar características, como métodos o propiedades, que no están disponibles en las interfaces estándar `CodeModel` y `FileCodeModel`, cree su propia interfaz que herede de la estándar. Asegúrese de documentarlo con el sistema del proyecto para que los usuarios finales sepan buscarlo. Se devuelve la interfaz estándar, pero el usuario puede llamar al método `QueryInterface` o convertir a la interfaz si se sabe que existe.

## <a name="see-also"></a>Vea también
- [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)