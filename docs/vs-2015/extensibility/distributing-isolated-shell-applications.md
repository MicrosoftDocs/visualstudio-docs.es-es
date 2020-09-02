---
title: Distribución de aplicaciones de Shell aislado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204677"
---
# <a name="distributing-isolated-shell-applications"></a>Distribución de aplicaciones de Shell aislado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debe instalar Visual Studio y el SDK de Visual Studio para crear una aplicación de Shell aislado. Para distribuir la aplicación a los equipos de otros usuarios o clientes, debe incluir un paquete redistribuible especial para el shell aislado.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Requisitos previos para la distribución de aplicaciones de Shell aislado  
  
|Nombre|Descripción|  
|----------|-----------------|  
|Visual Studio SDK|El SDK que debe tener para desarrollar y probar las extensiones de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . También puede usar el SDK para crear su propia instancia del shell aislado de Visual Studio.<br /><br /> Visual Studio es un requisito previo para el SDK.|  
|Microsoft Visual Studio redistribuible de Shell aislado|El redistribuible que se incluye en el programa de instalación al compilar un entorno de herramientas en el shell aislado de Visual Studio. El paquete redistribuible de Shell aislado incluye el .NET Framework 4,5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Crear un programa de instalación para la aplicación  
 Debe crear un programa de instalación especial para su aplicación de Shell integrada o aislada. Para obtener más información, vea [instalar una aplicación de Shell aislado](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Permitir actualizaciones en la aplicación  
 El programa de instalación debe permitir la posibilidad de que se actualice la aplicación, ya sea por Microsoft Update o por las actualizaciones de su empresa. Para obtener más información sobre las actualizaciones, vea [instrucciones de mantenimiento para las aplicaciones de Shell aislado](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
