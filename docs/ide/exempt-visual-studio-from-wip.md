---
title: Exención de Windows Information Protection
ms.date: 06/01/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b4eb454f641b5bef7273464d605fb194f650790
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588569"
---
# <a name="configure-visual-studio-as-a-wip-exempt-app"></a>Configurar Visual Studio como una aplicación exenta de WIP

[Windows Information Protection](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip) (WIP) contribuye a la protección contra la pérdida de datos empresariales a través de aplicaciones, como el correo electrónico, las redes sociales y la nube pública, que están fuera del control de la empresa. WIP ayuda a protegerse contra la pérdida accidental de datos en dispositivos propiedad de la empresa y personales, sin necesidad de realizar cambios en su entorno u otras aplicaciones.

Las aplicaciones *habilitadas* para WIP deben evitar que los datos empresariales acaben en ubicaciones de red desprotegidas, así como el cifrado de datos personales. Visual Studio no es una aplicación habilitada, por lo que no funciona en entornos de WIP habilitado a menos que la exentas. Siga los pasos descritos en este artículo para permitir que Visual Studio funcione en un equipo habilitado para WIP.

## <a name="configure-vs-as-a-wip-exempt-app"></a>Configurar VS como una aplicación exenta de WIP

Puede excluir a Visual Studio de las restricciones de WIP, pero permitirle que use datos empresariales. Las aplicaciones exentas de WIP pueden conectarse a recursos de empresa en la nube mediante una dirección IP o un nombre de host. No se aplica cifrado y la aplicación puede tener acceso a archivos locales.

Para excluir a Visual Studio de WIP, siga los [pasos para excluir una aplicación de escritorio](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#exempt-apps-from-a-wip-policy).

## <a name="create-a-wip-exempt-applocker-policy-file"></a>Cree un archivo de directiva de AppLocker exento de WIP

Dado que Visual Studio incluye varios archivos binarios, [cree un archivo de directiva de AppLocker exento de WIP](/windows/security/threat-protection/windows-defender-application-control/applocker/run-the-automatically-generate-rules-wizard). AppLocker permite generar automáticamente reglas para todos los archivos dentro de una carpeta.

## <a name="add-appcompat-to-the-enterprise-cloud-resource-policy"></a>Agregar AppCompat a la directiva de recursos de empresa en la nube

Para especificar dónde puede acceder Visual Studio a datos empresariales en la red, siga estos [pasos para definir las ubicaciones donde las aplicaciones protegidas pueden buscar y enviar datos empresariales](/windows/security/information-protection/windows-information-protection/create-wip-policy-using-intune-azure#choose-where-apps-can-access-enterprise-data). Para impedir que Windows bloquee las conexiones a recursos en la nube a través de una dirección IP, asegúrese de agregar la cadena /\*AppCompat\* a la configuración.

## <a name="see-also"></a>Vea también

- [Comportamiento de aplicaciones con WIP](/windows/security/information-protection/windows-information-protection/app-behavior-with-wip)
