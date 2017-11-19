---
title: "Prácticas recomendadas para la seguridad en VSPackages | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 770dff4b531bf4a7347cb648ca4c930b28b79bea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="best-practices-for-security-in-vspackages"></a>Prácticas recomendadas de seguridad en los paquetes VSPackage
Para instalar el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] en el equipo, debe estar ejecutando en un contexto con credenciales administrativas. La unidad básica de seguridad e implementación de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplicación es el [VSPackages](../../extensibility/internals/vspackages.md). Un VSPackage debe registrarse mediante el uso de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], lo que también requiere credenciales administrativas.  
  
 Los administradores tienen todos los permisos que se va a escribir en el registro y el sistema de archivos como ejecutar cualquier código. Debe tener permisos para desarrollar, implementar o instalar un paquete VSPackage.  
  
 Tan pronto como se instala, un VSPackage es de plena confianza. Debido a este alto nivel de permiso asociada a un paquete VSPackage, es posible instalar involuntariamente un VSPackage que tiene métodos maliciosos.  
  
 Los usuarios deben asegurarse de que instalar VSPackages únicamente de orígenes de confianza. Las empresas que desarrollan VSPackages fuertemente deben nombre e inicia su sesión garantizar que el usuario que la manipulación se impide. Las empresas que desarrollan VSPackages deben examinar sus dependencias externas, como servicios web y la instalación remota, para evaluar y corregir cualquier problema de seguridad.  
  
 Para obtener más información, vea instrucciones de codificación segura para .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Vea también  
 [Complemento de seguridad](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Seguridad DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)