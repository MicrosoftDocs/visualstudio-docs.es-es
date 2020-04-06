---
title: Prácticas recomendadas para la seguridad en VSPackages Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709900"
---
# <a name="best-practices-for-security-in-vspackages"></a>Prácticas recomendadas para la seguridad en VSPackages
Para instalar [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] el equipo, debe estar ejecutándose en un contexto con credenciales administrativas. La unidad básica de seguridad [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e implementación de una aplicación es [el VSPackage](../../extensibility/internals/vspackages.md). Un VSPackage debe registrarse mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], que también requiere credenciales administrativas.

 Los administradores tienen permisos completos para escribir en el registro y el sistema de archivos, y para ejecutar cualquier código. Debe tener estos permisos para desarrollar, implementar o instalar un VSPackage.

 Tan pronto como se instala, un VSPackage es de plena confianza. Debido a este alto nivel de permiso asociado a un VSPackage, es posible instalar inadvertidamente un VSPackage que tiene intención malintencionada.

 Los usuarios deben asegurarse de que instalan VSPackages solo desde orígenes de confianza. Las empresas que desarrollan VSPackages deben nombrarlos y firmarlos fuertemente, para asegurar al usuario que se impide la manipulación. Las empresas que desarrollan VSPackages deben examinar sus dependencias externas, como servicios web e instalación remota, para evaluar y corregir cualquier problema de seguridad.

 Para obtener más información, vea Directrices de [codificación segura para .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Vea también
- [Seguridad de complementos](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Seguridad DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
