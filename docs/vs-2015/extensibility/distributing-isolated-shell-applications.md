---
title: Distribuir aplicaciones de Shell aislado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d05e6a88c9da52492a49462880a04e578feadb5c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305817"
---
# <a name="distributing-isolated-shell-applications"></a>Distribuir aplicaciones de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debe instalar Visual Studio y el SDK de Visual Studio para crear una aplicación de shell aislado. Para distribuir la aplicación a las máquinas de otros usuarios o clientes, debe incluir un paquete redistribuible especial para el shell aislado.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Requisitos previos para la distribución de aplicaciones de Shell aislado  
  
|nombre|Descripción|  
|----------|-----------------|  
|Visual Studio SDK|El SDK debe tener para desarrollar y probar las extensiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. También puede usar el SDK para crear su propia instancia del shell aislado de Visual Studio.<br /><br /> Visual Studio es un requisito previo para el SDK.|  
|Paquete redistribuible de Shell (aislado) Microsoft Visual Studio|El paquete redistribuible de incluir en el programa de instalación cuando se compila en un entorno de herramientas en Visual Studio shell (aislado). El paquete redistribuible de Shell aislado incluye .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Crear un programa de instalación para la aplicación  
 Debe crear un programa de instalación especiales para la aplicación de shell integrado o aislado. Para obtener más información, consulte [instalar una aplicación de Shell aislado](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Permitir que las actualizaciones de la aplicación  
 El programa de instalación debe permitir la posibilidad de que se actualizará la aplicación, las actualizaciones de Microsoft o las actualizaciones de su compañía. Para obtener más información acerca de las actualizaciones, consulte [mantenimiento directrices para las aplicaciones de Shell aislado](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).

