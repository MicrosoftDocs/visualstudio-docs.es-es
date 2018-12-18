---
title: Proveedor de símbolos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31bfba509081b47988e25beae79529df7f20a760
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758043"
---
# <a name="symbol-provider"></a>Proveedor de símbolos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Una implementación del evaluador de expresiones debe tener acceso a la información de depuración simbólica generada por el compilador de lenguaje con el fin de evaluar variables y expresiones. Lo hace si consume las interfaces de un proveedor de símbolos (SP), también denominado un controlador de símbolos.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Proporciona SPs para código administrado, así como código nativo utilizando el formato de archivo de símbolos de base de datos de programa (PDB). A menos que haya una fuerte necesita para que el programa para utilizar los símbolos que se almacenan en un formato personalizado, se recomienda utilizar el Service Pack proporcionada por [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="implementation-notes"></a>Notas de implementación  
 El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] motores de depuración que se esperan para comunicarse con el Service Pack mediante interfaces de Common Language Runtime (CLR). Como resultado, un Service Pack que trabajará con los motores de depuración de Visual Studio debe admitir el CLR. Encontrará una lista completa de todas las interfaces de depuración de CLR en debugref.doc, que forma parte de la [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)].  
  
 Si el SP funcionará sólo con el motor de depuración personalizado, puede implementar el SP como considere oportuno según las necesidades de su motor de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)

