---
title: "Prácticas recomendadas para la seguridad en VSPackages | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c7ceb884ad060ea45c0fd204b5611ce284d3d2af
ms.lasthandoff: 02/22/2017

---
# <a name="best-practices-for-security-in-vspackages"></a>Prácticas recomendadas de seguridad en VSPackages
Para instalar el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] en el equipo, debe estar ejecutando en un contexto con credenciales administrativas. La unidad básica de seguridad e implementación de un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplicación es el [VSPackages](../../extensibility/internals/vspackages.md). Se debe registrar un VSPackage utilizando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que también requiere credenciales administrativas.  
  
 Los administradores tienen permisos completos para escribir en el registro y el sistema de archivos y ejecutar cualquier código. Debe tener permisos para desarrollar, implementar o instalar un paquete VSPackage.  
  
 Tan pronto como se instala, un VSPackage es de plena confianza. Debido a este alto nivel de permiso asociado a un VSPackage, es posible instalar involuntariamente un VSPackage que tenga malas intenciones.  
  
 Los usuarios deben garantizar que se instalen VSPackages fuentes de confianza. Las empresas que desarrollan VSPackages fuertemente deben nombre y firmarlos garantizar que el usuario que la manipulación se impide. Las empresas que desarrollan VSPackages deben examinar sus dependencias externas, como servicios web y la instalación remota, para evaluar y corregir cualquier problema de seguridad.  
  
 Para obtener más información, consulte instrucciones de codificación segura para .NET Framework ([http://msdn.microsoft.com/library/d55zzx87.aspx](http://msdn.microsoft.com/library/d55zzx87.aspx)).  
  
## <a name="see-also"></a>Vea también  
 [Seguridad de complementos](http://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)   
 [Seguridad DDEX](http://msdn.microsoft.com/en-us/44a52a70-5c98-450e-993d-4a3b32f69ba8)
