---
title: Prácticas recomendadas de seguridad en VSPackages | Microsoft Docs
description: Obtenga información sobre los procedimientos recomendados para la seguridad en un VSPackage, la unidad básica de seguridad y la implementación de una aplicación de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cca66d6c1fce0deb8103a7d626c16a4e81bc7b5f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086214"
---
# <a name="best-practices-for-security-in-vspackages"></a>Prácticas recomendadas de seguridad en VSPackages
Para instalar [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] en el equipo, debe ejecutar en un contexto con credenciales administrativas. La unidad básica de seguridad y la implementación de una [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aplicación es el [VSPackage](../../extensibility/internals/vspackages.md). Un VSPackage debe registrarse mediante [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , que también requiere credenciales administrativas.

 Los administradores tienen permisos completos para escribir en el registro y el sistema de archivos, y para ejecutar cualquier código. Debe tener estos permisos para desarrollar, implementar o instalar un VSPackage.

 En cuanto se instala, un VSPackage es de plena confianza. Debido a este alto nivel de permiso asociado a un VSPackage, es posible instalar accidentalmente un VSPackage con intenciones maliciosas.

 Los usuarios deben asegurarse de que instalan VSPackages únicamente desde orígenes de confianza. Las compañías que desarrollan VSPackages deben asignarles un nombre seguro y firmarlos para garantizar el usuario de que se impide la manipulación. Las compañías que desarrollan VSPackages deben examinar sus dependencias externas, como los servicios web y la instalación remota, para evaluar y corregir cualquier problema de seguridad.

 Para obtener más información, vea [instrucciones de codificación segura para el .NET Framework](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90)).

## <a name="see-also"></a>Consulte también
- [Seguridad de complementos](/previous-versions/1326zbk3(v=vs.140))
- [Seguridad de DDEX](/previous-versions/bb163703(v=vs.140))