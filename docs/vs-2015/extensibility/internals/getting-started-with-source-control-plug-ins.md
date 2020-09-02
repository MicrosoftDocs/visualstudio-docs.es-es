---
title: Introducción con complementos de control de código fuente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85aa5727f252ad75c45064d7b885e3d282da36a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538166"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Introducción a los complementos de control de código fuente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Para crear un complemento de control de código fuente, debe crear un archivo DLL que implemente las funciones definidas en la API del complemento de control de código fuente y, a continuación, registrar el archivo DLL con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para que esté disponible para su uso en el control de versiones de código fuente.  
  
 Tres versiones de la API del complemento de control de código fuente (versiones 1,1, 1,2 y 1,3) están disponibles para los complementos de control de código fuente. La API del complemento de control de código fuente documentada aquí es la versión 1,3. Se diseñó para ser totalmente compatible con los complementos de control de código fuente compatibles con las versiones 1,1 y 1,2. La sección [novedades de la API del complemento de control de código fuente versión 1,3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) detalla las nuevas características admitidas en la versión más reciente de la API del complemento de control de código fuente.  
  
## <a name="in-this-section"></a>En esta sección  
 [Instalación de un complemento de control de código fuente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Describe cómo realizar las entradas del registro necesarias para conectar una DLL de control de código fuente.  
  
 [Novedades de la API del complemento de control de código fuente, versión 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Proporciona una breve introducción a los cambios que se realizaron en la API del complemento de control de código fuente en la versión 1,3.  
  
 [Novedades de la API del complemento de control de código fuente, versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Proporciona una breve introducción a los cambios que se realizaron en la API del complemento de control de código fuente en la versión 1,2.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Complementos de control de código fuente](../../extensibility/source-control-plug-ins.md)  
 Proporciona una lista completa de todos los elementos de la API del complemento de control de código fuente.  
  
 [Creación de un complemento de control de código fuente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Define el SDK del complemento de control de código fuente y describe los recursos incluidos.
