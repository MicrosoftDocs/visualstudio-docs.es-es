---
title: Agregar publicador de confianza al cuadro cliente (ClickOnce)
description: Obtenga información acerca de cómo agregar un certificado a un equipo cliente para que las aplicaciones ClickOnce se ejecuten en un nivel de confianza superior sin preguntar al usuario.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c04b8d700d7739f0e4ef1fba259aab0595cea28c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947821"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Procedimientos para agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce
Con la implementación de aplicaciones de confianza, puede configurar equipos cliente para que las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se ejecuten con un nivel superior de confianza sin preguntar al usuario. En los procedimientos siguientes se muestra cómo usar la herramienta de línea de comandos CertMgr.exe para agregar el certificado de un publicador al almacén de publicadores de confianza de un equipo cliente.

 Los comandos que se usan varían ligeramente si la entidad de certificación (CA) que emitió el certificado forma parte de la raíz de confianza del cliente. Si un equipo cliente de Windows forma parte de un dominio, contendrá en una lista las CA que se consideren raíces de confianza. Suele ser el administrador del sistema quien configura esta lista. Si el certificado fue emitido por una de estas raíces de confianza o por una CA vinculada a una raíz de confianza, puede agregar el certificado al almacén raíz de confianza del cliente. En cambio, si el certificado no fue emitido por una de estas raíces de confianza, debe agregarlo al almacén raíz de confianza y al almacén de publicadores de confianza del cliente.

> [!NOTE]
> Debe agregar los certificados de esta manera en todos los equipos cliente en los que quiera implementar una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que requiere permisos elevados. Puede agregar los certificados manualmente o mediante una aplicación implementada en los clientes. Solo tiene que configurar estos equipos una vez, tras lo cual puede implementar cualquier número de aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] firmadas con el mismo certificado.

 También puede agregar un certificado a un almacén mediante programación a través de la clase <xref:System.Security.Cryptography.X509Certificates.X509Store> .

 Para obtener información general sobre la implementación de aplicaciones de confianza, vea [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Para agregar un certificado al almacén de publicadores de confianza en la raíz de confianza

1. Obtenga un certificado digital de una CA.

2. Exporte el certificado en el formato Base64 X.509 (*.cer*). Para obtener más información sobre los formatos de certificado, vea [Exportar un certificado](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. Desde el símbolo del sistema en los equipos cliente, ejecute el comando siguiente:

     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Para agregar un certificado al almacén de publicadores de confianza en una raíz diferente

1. Obtenga un certificado digital de una CA.

2. Exporte el certificado en el formato Base64 X.509 (*.cer*). Para obtener más información acerca de los formatos de certificado, consulte [exportar un certificado](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. Desde el símbolo del sistema en los equipos cliente, ejecute el comando siguiente:

     **certmgr.exe -add good.cer -c -s -r localMachine Root**

     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**

## <a name="see-also"></a>Vea también
- [Tutorial: Implementación manual de una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Protección de las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)
- [Seguridad de acceso del código para aplicaciones ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce y Authenticode](../deployment/clickonce-and-authenticode.md)
- [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md)
- [Cómo: habilitar la configuración de seguridad de ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Cómo: establecer una zona de seguridad para una aplicación ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Cómo: establecer permisos personalizados para una aplicación ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Procedimientos para depurar una aplicación ClickOnce con permisos restringidos](securing-clickonce-applications.md)
- [Procedimientos para agregar un publicador de confianza a un equipo cliente para aplicaciones ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Procedimientos para volver a firmar manifiestos de aplicación e implementación](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Procedimientos para configurar el comportamiento del mensaje relativo a la confianza de ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)