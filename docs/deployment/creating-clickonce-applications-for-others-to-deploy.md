---
title: Crear aplicaciones ClickOnce para que otros usuarios para implementar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01e85c0257d372fa9b27ec5f031aae61132f7edc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928909"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Creación de aplicaciones ClickOnce para que las implementen terceros
No todos los desarrolladores que crean las implementaciones de ClickOnce plan implementar las propias aplicaciones. Muchos de ellos simplemente empaquetan su aplicación mediante ClickOnce y, a continuación, transfiera los archivos a un cliente, como una corporación grande. El cliente pasa a ser el responsable de alojar la aplicación en su red. En este tema se describe algunos de los problemas inherentes a tales implementaciones en las versiones de .NET Framework anteriores a la versión 3.5. A continuación, se describe una nueva solución proporcionada mediante el uso de la nueva característica de "Usar manifiesto de confianza" en .NET Framework 3.5. Finalmente, concluye con las estrategias recomendadas para la creación de implementaciones de ClickOnce para los clientes que aún utilicen versiones anteriores de .NET Framework.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemas relacionados con la creación de implementaciones para los clientes
 Cuando se planea suministrar una implementación a un cliente, se producen varios problemas. El primer problema afecta a la firma de código. Para ser implementados a través de una red, el manifiesto de implementación y el manifiesto de aplicación de una implementación de ClickOnce deben ambos firmarse con un certificado digital. Esto plantea la pregunta de si debe usar el certificado del desarrollador o del cliente al firmar los manifiestos.

 Es fundamental, la pregunta de qué certificado utilizar como identidad de la aplicación ClickOnce se basa en la firma digital del manifiesto de implementación. Si el desarrollador firma el manifiesto de implementación, podría provocar conflictos si el cliente es una compañía grande y más de una división de la organización implementa una versión personalizada de la aplicación.

 Por ejemplo, supongamos que Adventure Works tiene un departamento de finanzas y un departamento de recursos humanos. Una aplicación ClickOnce de Microsoft Corporation, que genera informes de datos almacenados en una base de datos SQL de licencia de ambos departamentos. Microsoft proporciona a cada departamento con una versión de la aplicación que se personaliza para sus datos. Si las aplicaciones están firmadas con el mismo certificado de Authenticode, un usuario que intenta usar ambas aplicaciones podría producirse un error, como ClickOnce consideraría la segunda aplicación sea idéntico al primero. En este caso, el cliente podría experimentar efectos secundarios imprevisibles y no deseados que incluyen la pérdida de los datos almacenados localmente por la aplicación.

 Otro problema relacionado para la firma de código es el `deploymentProvider` elemento en el manifiesto de implementación, que indica dónde debe buscar actualizaciones de la aplicación de ClickOnce. Este elemento debe agregarse al manifiesto de implementación antes de firmar. Si este elemento se agrega a continuación, el manifiesto de implementación debe volver a firmarse.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Requieren que el cliente firmar el manifiesto de implementación
 Una solución a este problema de implementaciones no único es que el programador firme el manifiesto de aplicación y el cliente firmar el manifiesto de implementación. Aunque este enfoque funciona, presenta otros problemas. Puesto que un certificado de Authenticode debe permanecer un recurso protegido, el cliente no puede devolver el certificado para el desarrollador para firmar la implementación. Mientras que el cliente puede firmar el manifiesto de implementación a sí mismos mediante el uso de las herramientas disponibles de forma gratuita con el SDK de .NET Framework, esto puede requerir conocimientos técnicos más que el cliente está dispuesto o puede proporcionar. En tales casos, el desarrollador crea normalmente una aplicación, el sitio Web o el otro mecanismo a través del cual el cliente puede enviar su versión de la aplicación para la firma.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>El impacto de la firma del cliente en la seguridad de la aplicación ClickOnce
 Incluso si el desarrollador y el cliente acepta que el cliente debe firmar el manifiesto de aplicación, esto provoca otros problemas que rodean la identidad de la aplicación, especialmente a medida que se aplica a la implementación de aplicaciones de confianza. (Para obtener más información sobre esta característica, consulte [información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).) Supongamos que Adventure Works desea configurar sus equipos cliente para que se ejecute cualquier aplicación proporcionado por Microsoft Corporation con plena confianza. Si Adventure Works firma el manifiesto de implementación, ClickOnce usará firma de seguridad de Adventure Works para determinar el nivel de confianza de la aplicación.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Crear implementaciones de cliente mediante el uso de manifiesto de aplicación de confianza
 ClickOnce en .NET Framework 3.5 incluye una nueva característica que proporciona a los desarrolladores y los clientes una solución nueva para el escenario de cómo se deben firman los manifiestos. El manifiesto de aplicación ClickOnce admite un nuevo elemento denominado `<useManifestForTrust>` que permite que un desarrollador indicar que la firma digital del manifiesto de aplicación es lo que debe usarse para tomar decisiones de confianza. El programador usa las herramientas de empaquetado de ClickOnce, tales como *Mage.exe*, *MageUI.exe*y Visual Studio, debe incluir este elemento en el manifiesto de aplicación, así como para incrustar tanto su nombre de publicador y el nombre de la aplicación en el manifiesto.

 Cuando se usa `<useManifestForTrust>`, el manifiesto de implementación no tiene que estar firmado con un certificado de Authenticode emitido por una entidad de certificación. En su lugar, pueden estar firmado con lo que se conoce como un certificado autofirmado. Un certificado autofirmado es generado por el cliente o el desarrollador mediante herramientas estándar de .NET Framework SDK y, a continuación, se aplica al manifiesto de implementación mediante el uso de las herramientas de implementación estándares de ClickOnce. Para obtener más información, consulte [MakeCert](/windows/desktop/SecCrypto/makecert).

 Usar un certificado autofirmado para el manifiesto de implementación presenta varias ventajas. Al eliminar la necesidad del cliente obtener o crear su propio certificado Authenticode, `<useManifestForTrust>` simplifica la implementación del cliente, permitiendo al desarrollador mantener su propia identidad de marca en la aplicación. El resultado es un conjunto de implementaciones con signo que son más seguras y que tienen identidades de aplicación único. Esto elimina el posible conflicto que puede producirse al implementar la misma aplicación para varios clientes.

 Para obtener información detallada sobre cómo crear una implementación de ClickOnce con `<useManifestForTrust>` habilitado, consulte [Tutorial: Implementar manualmente una aplicación ClickOnce que no requiere volver a firmar y que conserve la información de personalización de marca](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Cómo funciona el manifiesto de aplicación de confianza en tiempo de ejecución
 Para obtener una mejor comprensión de cómo usar el manifiesto de aplicación de confianza funciona en tiempo de ejecución, considere el ejemplo siguiente. Microsoft crea una aplicación ClickOnce que tiene como destino .NET Framework 3.5. El manifiesto de aplicación usa el `<useManifestForTrust>` elemento y está firmado por Microsoft. Adventure Works firma el manifiesto de implementación mediante un certificado autofirmado. Los clientes de Adventure Works están configurados para confiar en cualquier aplicación firmada por Microsoft.

 Cuando un usuario hace clic en un vínculo al manifiesto de implementación, ClickOnce instala la aplicación en el equipo del usuario. La información del certificado y la implementación de identificar de forma única la aplicación ClickOnce en el equipo cliente. Si el usuario intenta volver a instalar la misma aplicación desde una ubicación diferente, ClickOnce puede usar esta identidad para determinar que la aplicación ya existe en el cliente.

 A continuación, ClickOnce examina el certificado de Authenticode que se usa para firmar el manifiesto de aplicación, que determina el nivel de confianza que se concederá ClickOnce. Puesto que Adventure Works ha configurado sus clientes para que confíe en cualquier aplicación firmada por Microsoft, esta aplicación ClickOnce se concede plena confianza. Para más información, vea [Introducción a la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Crear implementaciones de cliente para las versiones anteriores
 ¿Qué ocurre si un programador está implementando aplicaciones ClickOnce para los clientes que usan versiones anteriores de .NET Framework? Las siguientes secciones resumen varias soluciones recomendadas, junto con las ventajas y desventajas de cada uno.

### <a name="sign-deployments-on-behalf-of-customer"></a>Implementaciones de inicio de sesión en nombre de cliente
 Es una estrategia de implementación posibles para que el desarrollador crear un mecanismo para firmar las implementaciones en nombre de sus clientes, mediante el uso de la clave privada del cliente. Esto impide que el desarrollador tenga que administrar claves privadas o varios paquetes de implementación. El desarrollador simplemente proporciona la misma implementación para cada cliente. Es responsabilidad del cliente para personalizarlo para su entorno mediante el servicio de firmado.

 Un inconveniente de este método es el tiempo y gastos que son necesarios para implementarla. Aunque este tipo de servicio se puede compilar mediante el uso de las herramientas proporcionadas en .NET Framework SDK, agregará más tiempo de desarrollo para el ciclo de vida del producto.

 Como se indicó anteriormente en este tema, otra desventaja es que la versión de cada cliente de la aplicación tendrá la misma identidad de aplicación, lo que puede provocar conflictos. Si se trata de un problema, el desarrollador puede cambiar el campo de nombre que se usa al generar el manifiesto de implementación para proporcionar un nombre único a cada aplicación. Esto creará una identidad diferente para cada versión de la aplicación y eliminar cualquier conflicto potencial de identidad. Este campo se corresponde con el `-Name` argumentos de Mage.exe y a la **nombre** campo el **nombre** ficha en MageUI.exe.

 Por ejemplo, supongamos que el desarrollador ha creado una aplicación denominada Aplicación1. En lugar de crear una sola implementación con el campo de nombre establecido en Application1, el desarrollador puede crear varias implementaciones con una variación específica del cliente en este nombre, por ejemplo, Aplicación1-clientea, Aplicación1-ClienteB y así sucesivamente.

### <a name="deploy-using-a-setup-package"></a>Implementar mediante un paquete de instalación
 Una estrategia de implementación posibles segundo consiste en generar un proyecto de Setup de Microsoft para llevar a cabo la implementación inicial de la aplicación ClickOnce. Esto se puede proporcionar en uno de varios formatos diferentes: como una implementación de MSI, como un programa de instalación ejecutable (. (EXE), o como un archivo contenedor (.cab) junto con un script por lotes.

 Con esta técnica, el desarrollador podría proporcionar al cliente una implementación que incluya los archivos de aplicación, el manifiesto de aplicación y un manifiesto de implementación que actúa como una plantilla. El cliente podría ejecutar el programa de instalación que se les pedirá para una dirección URL de implementación (el servidor o recurso compartido de ubicación desde la que los usuarios instalan la aplicación ClickOnce), así como un certificado digital. También puede solicitar las opciones de configuración de ClickOnce adicionales, como el intervalo de comprobación de actualización de la aplicación de instalación. Una vez que esta información se recopila, el programa de instalación podría generar el manifiesto de implementación real, firmarlo y publicar la aplicación ClickOnce en la ubicación del servidor designado.

 Hay tres maneras de que el cliente pueda firmar el manifiesto de implementación en esta situación:

1. El cliente puede usar un certificado válido emitido por una entidad de certificación (CA).

2. Como una variación de este enfoque, el cliente puede firmar el manifiesto de implementación con un certificado autofirmado. El inconveniente de esto es que hará que la aplicación mostrar las palabras "Editor desconocido" cuando el usuario se le pregunte si desea instalarlo. Sin embargo, la ventaja es que impide que a los clientes menores de tener que dedicar tiempo y dinero necesarios para obtener un certificado emitido por una entidad de certificación.

3. Por último, el desarrollador puede incluir su propio certificado autofirmado en el paquete de instalación. Esto presenta los posibles problemas con la identidad de aplicación mencionados anteriormente en este tema.

   La desventaja para el método de proyecto de implementación de instalación es el tiempo y gastos necesarios para compilar una aplicación de implementación personalizado.

### <a name="have-customer-generate-deployment-manifest"></a>Tiene el cliente genere el manifiesto de implementación
 Una tercer posible estrategia de implementación consiste en desactivar solo la aplicación de archivos y aplicación de manifiesto al cliente. En este escenario, el cliente es responsable de usar el SDK de .NET Framework para generar y firmar el manifiesto de implementación.

 El inconveniente de este método es que requiere el cliente para instalar las herramientas del SDK de .NET Framework y que un desarrollador o administrador del sistema con experiencia en su uso. Algunos clientes pueden solicitar una solución que requiere poco o ningún esfuerzo técnico por su parte.

## <a name="see-also"></a>Vea también
- [Implementar aplicaciones ClickOnce para los servidores de pruebas y producción sin nueva firma](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Tutorial: Implementación manual de una aplicación ClickOnce que no requiera el proceso de volver a firmar y que conserve la información de marca comercial](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)