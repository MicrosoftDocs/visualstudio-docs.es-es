---
title: Crear aplicaciones ClickOnce para que las implementen otras | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ff76fe46f07ef713cb3c0e529e8029730450f2a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675602"
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Crear aplicaciones ClickOnce para que las implementen terceros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No todos los desarrolladores que están creando implementaciones ClickOnce planean implementar las propias aplicaciones. Muchos de ellos simplemente empaquetan su aplicación mediante ClickOnce y, a continuación, entregan los archivos a un cliente, como una corporación grande. El cliente se convierte en el responsable de hospedar la aplicación en su red. En este tema se describen algunos de los problemas inherentes a estas implementaciones en las versiones de los .NET Framework anteriores a la versión 3,5. A continuación, describe una nueva solución que se proporciona mediante la nueva característica "usar manifiesto para confianza" en el .NET Framework 3,5. Por último, concluye con las estrategias recomendadas para crear implementaciones ClickOnce para los clientes que aún usan versiones anteriores de la .NET Framework.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemas relacionados con la creación de implementaciones para clientes  
 Se producen varios problemas al planear la entrega de una implementación a un cliente. El primer problema se refiere a la firma de código. Para implementarse en una red, el manifiesto de implementación y el manifiesto de aplicación de una implementación ClickOnce deben estar firmados con un certificado digital. Esto plantea la pregunta de si se debe usar el certificado del desarrollador o el certificado del cliente al firmar los manifiestos.  
  
 La pregunta de qué certificado usar es fundamental, ya que la identidad de la aplicación ClickOnce se basa en la firma digital del manifiesto de implementación. Si el desarrollador firma el manifiesto de implementación, podría provocar conflictos si el cliente es una empresa grande y más de una división de la empresa implementa una versión personalizada de la aplicación.  
  
 Por ejemplo, suponga que Adventure Works tiene un departamento de finanzas y un departamento de recursos humanos. Ambos departamentos tienen una licencia de aplicación ClickOnce de Microsoft Corporation que genera informes a partir de los datos almacenados en una base de datos SQL. Microsoft proporciona a cada departamento una versión de la aplicación que se ha personalizado para sus datos. Si las aplicaciones están firmadas con el mismo certificado Authenticode, un usuario que intente usar ambas aplicaciones encontraría un error, ya que ClickOnce consideraría que la segunda aplicación es idéntica a la primera. En este caso, el cliente podría experimentar efectos secundarios imprevisibles y no deseados que incluyen la pérdida de los datos almacenados localmente por la aplicación.  
  
 Un problema adicional relacionado con la firma de código es el `deploymentProvider` elemento en el manifiesto de implementación, que indica a ClickOnce dónde buscar las actualizaciones de la aplicación. Este elemento tiene que agregarse al manifiesto de implementación antes de su firma. Si este elemento se agrega después, se debe volver a firmar el manifiesto de implementación.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Requerir al cliente que firme el manifiesto de implementación  
 Una solución a este problema de las implementaciones no únicas es hacer que el desarrollador firme el manifiesto de aplicación y que el cliente firme el manifiesto de implementación. Aunque este enfoque funciona, introduce otros problemas. Puesto que un certificado Authenticode debe permanecer en un recurso protegido, el cliente no puede simplemente dar el certificado al desarrollador para firmar la implementación. Aunque el cliente puede firmar el manifiesto de implementación con las herramientas que están disponibles de forma gratuita con el SDK de .NET Framework, esto puede requerir más conocimientos técnicos de los que el cliente está dispuesto a proporcionar. En tales casos, el desarrollador normalmente crea una aplicación, un sitio web u otro mecanismo a través del cual el cliente puede enviar su versión de la aplicación para firmar.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Impacto de la firma del cliente en la seguridad de la aplicación ClickOnce  
 Incluso si el desarrollador y el cliente acuerdan que el cliente debe firmar el manifiesto de aplicación, genera otros problemas que rodean la identidad de la aplicación, sobre todo cuando se aplica a la implementación de aplicaciones de confianza. (Para obtener más información acerca de esta característica, consulte [información general](../deployment/trusted-application-deployment-overview.md)sobre la implementación de aplicaciones de confianza). Suponiendo que Adventure Works desea configurar sus equipos cliente para que cualquier aplicación proporcionada por Microsoft Corporation se ejecute con plena confianza. Si Adventure Works firma el manifiesto de implementación, ClickOnce usará la firma de seguridad del trabajo de Adventure Works para determinar el nivel de confianza de la aplicación.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Creación de implementaciones de clientes mediante el manifiesto de aplicación para confianza  
 ClickOnce en el .NET Framework 3,5 contiene una nueva característica que proporciona a los desarrolladores y clientes una nueva solución para el escenario de cómo se deben firmar los manifiestos. El manifiesto de aplicación ClickOnce admite un nuevo elemento denominado `<useManifestForTrust>` que permite a un programador indicar que la firma digital del manifiesto de aplicación es lo que se debe usar para tomar decisiones de confianza. El desarrollador utiliza herramientas de empaquetado ClickOnce, como Mage.exe, MageUI.exe y Visual Studio, para incluir este elemento en el manifiesto de aplicación, así como para insertar el nombre del publicador y el nombre de la aplicación en el manifiesto.  
  
 Al usar `<useManifestForTrust>` , el manifiesto de implementación no tiene que estar firmado con un certificado Authenticode emitido por una entidad de certificación. En su lugar, se puede firmar con lo que se conoce como certificado autofirmado. El cliente o el desarrollador genera un certificado autofirmado mediante las herramientas estándar del SDK de .NET Framework y, a continuación, se aplica al manifiesto de implementación mediante las herramientas de implementación estándar de ClickOnce. Para obtener más información, vea [Makecert.exe (herramienta de creación de certificados)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
 El uso de un certificado autofirmado para el manifiesto de implementación presenta varias ventajas. Al eliminar la necesidad de que el cliente obtenga o cree su propio certificado Authenticode, `<useManifestForTrust>` simplifica la implementación para el cliente, a la vez que permite al desarrollador mantener su propia identidad de personalización de marca en la aplicación. El resultado es un conjunto de implementaciones con firma que son más seguras y tienen identidades de aplicación únicas. Esto elimina el posible conflicto que puede producirse al implementar la misma aplicación en varios clientes.  
  
 Para obtener información paso a paso sobre cómo crear una implementación ClickOnce con `<useManifestForTrust>` habilitada, vea [Tutorial: implementar manualmente una aplicación ClickOnce que no requiera volver a firmar y que conserve la información de personalización de marca](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Cómo funciona el manifiesto de aplicación para confianza en tiempo de ejecución  
 Para comprender mejor cómo funciona el manifiesto de aplicación para confianza en tiempo de ejecución, considere el ejemplo siguiente. Microsoft crea una aplicación ClickOnce que tiene como destino el .NET Framework 3,5. El manifiesto de aplicación utiliza el `<useManifestForTrust>` elemento y está firmado por Microsoft. Adventure Works firma el manifiesto de implementación mediante un certificado autofirmado. Los clientes de Adventure Works están configurados para confiar en cualquier aplicación firmada por Microsoft.  
  
 Cuando un usuario hace clic en un vínculo al manifiesto de implementación, ClickOnce instala la aplicación en el equipo del usuario. La información de certificado e implementación identifica la aplicación de forma exclusiva en ClickOnce en el equipo cliente. Si el usuario intenta instalar de nuevo la misma aplicación desde una ubicación diferente, ClickOnce puede usar esta identidad para determinar que la aplicación ya existe en el cliente.  
  
 A continuación, ClickOnce examina el certificado de Authenticode que se usa para firmar el manifiesto de aplicación, que determina el nivel de confianza que concederá ClickOnce. Como Adventure Works ha configurado sus clientes para que confíen en cualquier aplicación firmada por Microsoft, a esta aplicación ClickOnce se le concede plena confianza. Para obtener más información, vea [información general sobre la implementación de aplicaciones de confianza](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Creación de implementaciones de clientes para versiones anteriores  
 ¿Qué ocurre si un desarrollador está implementando aplicaciones ClickOnce en clientes que usan versiones anteriores de la .NET Framework? En las secciones siguientes se resumen varias soluciones recomendadas, junto con las ventajas y desventajas de cada una.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Firmar implementaciones en nombre del cliente  
 Una posible estrategia de implementación es que el desarrollador cree un mecanismo para firmar las implementaciones en nombre de sus clientes, mediante el uso de la clave privada del cliente. Esto evita que el desarrollador tenga que administrar claves privadas o varios paquetes de implementación. El desarrollador solo proporciona la misma implementación a cada cliente. Depende del cliente personalizarlo para su entorno mediante el servicio de firma.  
  
 Un inconveniente de este método es el tiempo y los gastos necesarios para implementarlo. Aunque este servicio se puede compilar con las herramientas proporcionadas en el SDK de .NET Framework, agregará más tiempo de desarrollo al ciclo de vida del producto.  
  
 Como se indicó anteriormente en este tema, otro inconveniente es que la versión de la aplicación de cada cliente tendrá la misma identidad de aplicación, lo que podría provocar conflictos. Si esto supone un problema, el desarrollador puede cambiar el campo de nombre que se usa al generar el manifiesto de implementación para asignar un nombre único a cada aplicación. Esto creará una identidad independiente para cada versión de la aplicación y eliminará cualquier posible conflicto de identidad. Este campo corresponde al `-Name` argumento de Mage.exe y al campo de **nombre** de la pestaña **nombre** en MageUI.exe.  
  
 Por ejemplo, suponga que el desarrollador ha creado una aplicación denominada application1. En lugar de crear una única implementación con el campo nombre establecido en application1, el desarrollador puede crear varias implementaciones con una variación específica del cliente en este nombre, como application1-Customera, application1-Clienteb, etc.  
  
### <a name="deploy-using-a-setup-package"></a>Implementación mediante un paquete de instalación  
 Una segunda estrategia de implementación posible es generar un proyecto de instalación de Microsoft para realizar la implementación inicial de la aplicación ClickOnce. Se puede proporcionar en uno de varios formatos diferentes: como una implementación de MSI, como un archivo ejecutable de configuración (. EXE) o como un archivo contenedor (. cab) junto con un script por lotes.  
  
 Con esta técnica, el desarrollador proporcionaría al cliente una implementación que incluye los archivos de aplicación, el manifiesto de aplicación y un manifiesto de implementación que actúa como plantilla. El cliente ejecutaría el programa de instalación, que les solicitaría una dirección URL de implementación (el servidor o la ubicación del recurso compartido de archivos desde el que los usuarios instalarán la aplicación ClickOnce), así como un certificado digital. La aplicación de instalación también puede optar por solicitar opciones de configuración de ClickOnce adicionales, como el intervalo de comprobación de actualización. Una vez recopilada esta información, el programa de instalación generaría el manifiesto de implementación real, lo firmaría y publicaría la aplicación ClickOnce en la ubicación del servidor designada.  
  
 Hay tres formas de que el cliente pueda firmar el manifiesto de implementación en esta situación:  
  
1. El cliente puede usar un certificado válido emitido por una entidad de certificación (CA).  
  
2. Como variación de este enfoque, el cliente puede elegir firmar el manifiesto de implementación con un certificado autofirmado. El inconveniente de esto es que hará que la aplicación muestre las palabras "publicador desconocido" cuando se pregunte al usuario si desea instalarlo. Sin embargo, la ventaja es que impide que los clientes más pequeños tengan que dedicar el tiempo y el dinero necesarios a un certificado emitido por una entidad de certificación.  
  
3. Por último, el desarrollador puede incluir su propio certificado autofirmado en el paquete de instalación. Esto presenta los posibles problemas con la identidad de la aplicación que se explicó anteriormente en este tema.  
  
   El inconveniente del método de proyecto de implementación de instalación es el tiempo y los gastos necesarios para compilar una aplicación de implementación personalizada.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Hacer que el cliente genere el manifiesto de implementación  
 Una tercera estrategia de implementación posible consiste en entregar solo los archivos de aplicación y el manifiesto de aplicación al cliente. En este escenario, el cliente es responsable de usar el SDK de .NET Framework para generar y firmar el manifiesto de implementación.  
  
 El inconveniente de este método es que requiere que el cliente instale el .NET Framework herramientas del SDK y que tenga un desarrollador o administrador del sistema que tenga experiencia en su uso. Algunos clientes pueden solicitar una solución que requiera poco o ningún esfuerzo técnico por su parte.  
  
## <a name="see-also"></a>Consulte también  
 [Implementar aplicaciones ClickOnce para servidores de prueba y producción sin tener que volver a firmar](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Tutorial: implementar manualmente una aplicación ClickOnce que no requiera volver a firmar y que conserve la información de personalización de marca](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)
