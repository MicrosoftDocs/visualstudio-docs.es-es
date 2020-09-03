---
title: Prácticas recomendadas de seguridad en VSPackages | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709900"
---
# <a name="best-practices-for-security-in-vspackages"></a>Prácticas recomendadas de seguridad en VSPackages
Para instalar [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] en el equipo, debe ejecutar en un contexto con credenciales administrativas. La unidad básica de seguridad y la implementación de una [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplicación es el [VSPackage](../../extensibility/internals/vspackages.md). Un VSPackage debe registrarse mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , que también requiere credenciales administrativas.

 Los administradores tienen permisos completos para escribir en el registro y el sistema de archivos, y para ejecutar cualquier código. Debe tener estos permisos para desarrollar, implementar o instalar un VSPackage.

 En cuanto se instala, un VSPackage es de plena confianza. Debido a este alto nivel de permiso asociado a un VSPackage, es posible instalar accidentalmente un VSPackage con intenciones maliciosas.

 Los usuarios deben asegurarse de que instalan VSPackages únicamente desde orígenes de confianza. Las compañías que desarrollan VSPackages deben asignarles un nombre seguro y firmarlos para garantizar el usuario de que se impide la manipulación. Las compañías que desarrollan VSPackages deben examinar sus dependencias externas, como los servicios web y la instalación remota, para evaluar y corregir cualquier problema de seguridad.

 Para obtener más información, vea [instrucciones de codificación segura para el .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Vea también
- [Seguridad de complementos](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [Seguridad de DDEX](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
