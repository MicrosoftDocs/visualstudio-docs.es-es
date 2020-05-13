---
title: Proporcionar automatización para el código ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705992"
---
# <a name="providing-automation-for-code"></a>Provisión de automatización para código
No es necesario crear un modelo de automatización para el código. El SDK de entorno no proporciona un ejemplo para hacerlo. Para obtener información sobre <xref:EnvDTE.CodeModel> los modelos de código, consulte el objeto.

 Para implementar un modelo de código, debe implementar las interfaces que determine la estructura de datos interna. Los objetos deben derivarse de la `IDispatch` clase.

 Los objetos que <xref:EnvDTE.CodeModel> <xref:EnvDTE.FileCodeModel>se extienden <xref:EnvDTE.Project> y , están disponibles en el objeto y tienen el siguiente aspecto:

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 Puede optar por implementar `CodeModel` solo `FileCodeModel` la interfaz o `Project` la <xref:EnvDTE.ProjectItem> del objeto que devuelve de su y objetos. Proporcione cualquier funcionalidad de esta interfaz que sea adecuada para el sistema de proyectos.

 Si desea agregar características, como métodos o propiedades, que `CodeModel` `FileCodeModel` no están disponibles en el estándar y las interfaces, cree su propia interfaz que herede del estándar. Asegúrese de documentarlo con su sistema de proyecto para que los usuarios finales sepan que lo buscan. Devuelve la interfaz estándar, pero `QueryInterface` el usuario puede llamar al método o convertir a la interfaz si se sabe que existe.

## <a name="see-also"></a>Vea también
- [Información general del modelo de automatización](../../extensibility/internals/automation-model-overview.md)
