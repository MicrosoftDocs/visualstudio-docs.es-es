---
title: Distribuir aplicaciones de Shell aislado | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204677"
---
# <a name="distributing-isolated-shell-applications"></a>Distribución de aplicaciones de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debe instalar Visual Studio y el SDK de Visual Studio para crear una aplicación de shell aislado. Para distribuir la aplicación a las máquinas de otros usuarios o clientes, debe incluir un paquete redistribuible especial para el shell aislado.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Requisitos previos para la distribución de aplicaciones de Shell aislado  
  
|NOMBRE|DESCRIPCIÓN|  
|----------|-----------------|  
|Visual Studio SDK|El SDK debe tener para desarrollar y probar las extensiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. También puede usar el SDK para crear su propia instancia del shell aislado de Visual Studio.<br /><br /> Visual Studio es un requisito previo para el SDK.|  
|Paquete redistribuible de Shell (aislado) Microsoft Visual Studio|El paquete redistribuible de incluir en el programa de instalación cuando se compila en un entorno de herramientas en Visual Studio shell (aislado). El paquete redistribuible de Shell aislado incluye .NET Framework 4.5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Crear un programa de instalación para la aplicación  
 Debe crear un programa de instalación especiales para la aplicación de shell integrado o aislado. Para obtener más información, consulte [instalar una aplicación de Shell aislado](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Permitir que las actualizaciones de la aplicación  
 El programa de instalación debe permitir la posibilidad de que se actualizará la aplicación, las actualizaciones de Microsoft o las actualizaciones de su compañía. Para obtener más información acerca de las actualizaciones, consulte [mantenimiento directrices para las aplicaciones de Shell aislado](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
