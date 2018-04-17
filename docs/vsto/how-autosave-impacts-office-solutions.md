---
title: Cómo afecta a las soluciones de Office Autoguardado | Documentos de Microsoft
ms.custom: ''
ms.date: 07/20/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- autosave
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4492148420fd120d51013d24189e45cd2d8c45d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-autosave-impacts-office-solutions"></a>Cómo Autoguardado afecta a las soluciones de Office

Autoguardar es una característica de Excel, PowerPoint y Word que, cuando se activa, permite modificaciones del usuario se guarden automáticamente y continua. Si Autoguardado está desactivado, a continuación, guardar debe desencadenar manualmente para que los cambios del usuario que se deben conservar. Con la adición de esta característica, debe realizar ajustes en la solución de Office con el fin de asegurarse de que funciona sin problemas aunque Autoguardado está activado. Para obtener más información, consulte [Autoguardado cómo afecta a las macros y complementos](https://msdn.microsoft.com/vba/office-shared-vba/articles/how-autosave-impacts-addins-and-macros). Para obtener más información acerca de autoguardado en general, vea [¿qué es Autoguardado?](https://support.office.com/en-US/article/What-is-AutoSave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5).

Nota: Autoguardado para Windows Desktop Word, Excel y PowerPoint se introdujo en 2017 y está disponible para los suscriptores de Office 365. Los usuarios que han adquirido una licencia perpetua para Office 2016 o versiones anteriores no actualmente no tiene acceso a la característica co-autoría. (En línea de Excel, Excel para Android, Excel para iOS y móviles de Excel en la tienda Windows también admiten Autoguardado). 

## <a name="see-also"></a>Vea también
[Desarrollo de soluciones de Office](./developing-office-solutions.md)
