---
title: Procedimientos recomendados para la seguridad en VSPackages | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 629e7076335ee3cd9e2260d6242f586579bd8e0d
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370709"
---
# <a name="best-practices-for-security-in-vspackages"></a>Procedimientos recomendados de seguridad en VSPackages
Para instalar el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] en el equipo, debe ejecutar en un contexto con credenciales administrativas. La unidad básica de seguridad e implementación de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplicación es el [VSPackage](../../extensibility/internals/vspackages.md). Se debe registrar un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que también requiere credenciales administrativas.  
  
 Los administradores tienen permisos completos para escribir en el registro y sistema de archivos y para ejecutar cualquier código. Debe tener estos permisos para desarrollar, implementar o instalar un paquete VSPackage.  
  
 Tan pronto como se instala, un VSPackage es de plena confianza. Debido a este alto nivel de permiso asociado a un VSPackage, es posible instalar inadvertidamente un VSPackage que tenga propósitos maliciosos.  
  
 Los usuarios deben garantizar que se instalen los VSPackages únicamente desde orígenes de confianza. Las empresas de desarrollo de VSPackages fuertemente deben el nombre y firmarlos garantizar que el usuario que la manipulación se evita. Las empresas que desarrollan los paquetes VSPackage deben examinar sus dependencias externas, como servicios web y la instalación remota, para evaluar y corregir cualquier problema de seguridad.  
  
 Para obtener más información, consulte [segura de instrucciones de codificación de .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad de complementos](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Seguridad DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)