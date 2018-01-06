---
title: Crear aplicaciones ClickOnce para que otros usuarios para implementar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: d3a9762872f74b39d8cef387703488c01647dbcc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="creating-clickonce-applications-for-others-to-deploy"></a>Crear aplicaciones ClickOnce para que las implementen terceros
No todos los programadores que crean implementaciones ClickOnce plan implementar las propias aplicaciones. Muchos de ellos simplemente empaquetan su aplicación mediante ClickOnce y, a continuación, entregan los archivos a un cliente, por ejemplo, una gran empresa. El cliente pasa a ser el responsable de alojar la aplicación en su red. Este tema describen algunos de los problemas inherentes a tales implementaciones en las versiones de .NET Framework anteriores a la versión 3.5. A continuación, se describe una nueva solución que se proporciona mediante la nueva característica de "Usar manifiesto de confianza" en .NET Framework 3.5. Por último, concluye con estrategias recomendadas para crear implementaciones de ClickOnce para los clientes que aún utilicen versiones anteriores de .NET Framework.  
  
## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemas relacionados con la creación de implementaciones de clientes  
 Varios problemas se producen cuando se planea proporcionar una implementación a un cliente. El primer problema está relacionado con la firma de código. Para ser implementados a través de una red, el manifiesto de implementación y el manifiesto de aplicación de una implementación de ClickOnce deben tanto firmarse con un certificado digital. Esto provoca la pregunta de si se va a usar el certificado del desarrollador o el certificado del cliente al firmar los manifiestos.  
  
 La pregunta de qué certificado utilizar es crítica, como identidad de la aplicación ClickOnce se basa en la firma digital del manifiesto de implementación. Si el desarrollador firma el manifiesto de implementación, podría provocar conflictos si el cliente es una empresa grande y más de una división de la empresa implementa una versión personalizada de la aplicación.  
  
 Por ejemplo, supongamos que Adventure Works tiene un departamento de finanzas y un departamento de recursos humanos. Ambos departamentos otorgan licencias a una aplicación ClickOnce de Microsoft Corporation que genera informes de datos almacenados en una base de datos SQL. Microsoft proporciona a cada departamento con una versión de la aplicación que se personaliza para sus datos. Si las aplicaciones están firmadas con el mismo certificado Authenticode, un usuario que intenta utilizar ambas aplicaciones podría encontrar un error, como ClickOnce consideraría la segunda aplicación como idéntico al primero. En este caso, el cliente podría experimentar efectos secundarios imprevisibles y no deseados que incluyen la pérdida de los datos almacenados localmente por la aplicación.  
  
 Un problema adicional relacionado con firma de código es el `deploymentProvider` elemento en el manifiesto de implementación, que indica dónde debe buscar actualizaciones de la aplicación de ClickOnce. Este elemento debe agregarse al manifiesto de implementación antes de firmarlo. Si este elemento se agrega más adelante, el manifiesto de implementación debe volver a firmarse.  
  
### <a name="requiring-the-customer-to-sign-the-deployment-manifest"></a>Requerir que el cliente firmar el manifiesto de implementación  
 Una solución a este problema de implementaciones no es único es que el programador firme el manifiesto de aplicación y el cliente firmar el manifiesto de implementación. Si bien este enfoque funciona, presenta otros problemas. Puesto que un certificado Authenticode debe permanecer un recurso protegido, el cliente no puede simplemente dar el certificado al programador para firmar la implementación. Mientras que el cliente puede firmar el manifiesto de implementación por sí mismos mediante herramientas gratuitas disponibles con .NET Framework SDK, esto puede requerir conocimientos técnicos más que el cliente quiere o puede proporcionar. En tales casos, el programador suele crear una aplicación, sitio Web u otro mecanismo a través del cual el cliente puede enviar su versión de la aplicación para la firma.  
  
### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>El impacto de la firma del cliente en la seguridad de la aplicación ClickOnce  
 Aunque el programador y el cliente acepta que el cliente debe firmar el manifiesto de aplicación, esto provoca otros problemas que rodean la identidad de la aplicación, especialmente tal como se aplica a la implementación de aplicaciones de confianza. (Para obtener más información sobre esta característica, consulte [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).) Supongamos que Adventure Works desea configurar sus equipos cliente para que cualquier aplicación proporcionado por Microsoft Corporation se ejecute con plena confianza. Si Adventure Works firma el manifiesto de implementación, ClickOnce usará firma de seguridad de Adventure Works para determinar el nivel de confianza de la aplicación.  
  
## <a name="creating-customer-deployments-by-using-application-manifest-for-trust"></a>Crear implementaciones de cliente mediante el uso de manifiesto de aplicación de confianza  
 ClickOnce en .NET Framework 3.5 incluye una nueva característica que proporciona a los desarrolladores y los clientes una solución nueva para el escenario de cómo se deberían firmar los manifiestos. El manifiesto de aplicación ClickOnce admite un nuevo elemento denominado `<useManifestForTrust>` que permite que un desarrollador indicar que la firma digital del manifiesto de aplicación es lo que debe usarse para tomar decisiones de confianza. El programador usa herramientas de empaquetado de ClickOnce, como Mage.exe y MageUI.exe, Visual Studio, debe incluir este elemento en el manifiesto de aplicación, así como para insertar el nombre del publicador y el nombre de la aplicación en el manifiesto.  
  
 Cuando se usa `<useManifestForTrust>`, el manifiesto de implementación no tiene que estar firmado con un certificado Authenticode emitido por una entidad de certificación. En su lugar, se puede firmar con lo que se conoce como un certificado autofirmado. Un certificado autofirmado es generado por el cliente o el programador mediante el uso de herramientas estándar de .NET Framework SDK y, a continuación, se aplica al manifiesto de implementación mediante las herramientas de implementación estándares de ClickOnce. Para obtener más información, consulte [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx).  
  
 Usar un certificado autofirmado para el manifiesto de implementación presenta varias ventajas. Por lo que elimina la necesidad de que el cliente obtener o crear su propio certificado Authenticode, `<useManifestForTrust>` simplifica la implementación para el cliente, permitiendo al desarrollador mantener su propia identidad de marca en la aplicación. El resultado es un conjunto de implementaciones firmadas que son más seguras y tienen identidades de aplicación exclusivo. Esto elimina el posible conflicto que puede producirse al implementar la misma aplicación para varios clientes.  
  
 Para obtener información detallada sobre cómo crear una implementación de ClickOnce con `<useManifestForTrust>` habilitado, consulte [Tutorial: implementar manualmente una aplicación ClickOnce que Does no requieren nueva firma y esa información de personalización de marca conserva](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md).  
  
### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Manifiesto de la aplicación de confianza funciona en tiempo de ejecución  
 Para obtener una mejor comprensión de cómo usar el manifiesto de aplicación de confianza funciona en tiempo de ejecución, considere el ejemplo siguiente. Una aplicación ClickOnce que tiene como destino .NET Framework 3.5 es creada por Microsoft. El manifiesto de aplicación usa el `<useManifestForTrust>` elemento y firmados por Microsoft. Adventure Works firma el manifiesto de implementación mediante un certificado autofirmado. Los clientes de Adventure Works están configurados para confiar en cualquier aplicación firmada por Microsoft.  
  
 Cuando un usuario hace clic en un vínculo al manifiesto de implementación, ClickOnce instala la aplicación en el equipo del usuario. La información de implementación y de certificado identificar de forma única la aplicación ClickOnce en el equipo cliente. Si el usuario intenta volver a instalar la misma aplicación desde una ubicación diferente, ClickOnce puede usar esta identidad para determinar que la aplicación ya existe en el cliente.  
  
 A continuación, ClickOnce examina el certificado de Authenticode que se usa para firmar el manifiesto de aplicación, que determina el nivel de confianza que ClickOnce concederá. Puesto que Adventure Works ha configurado sus clientes para que confíen en cualquier aplicación firmada por Microsoft, esta aplicación ClickOnce se concede plena confianza. Para obtener más información, consulta [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="creating-customer-deployments-for-earlier-versions"></a>Crear implementaciones de clientes para versiones anteriores  
 ¿Qué ocurre si un programador está implementando aplicaciones ClickOnce para clientes que utilicen versiones anteriores de .NET Framework? Las siguientes secciones resumen varias soluciones recomendadas, junto con las ventajas y desventajas de cada uno.  
  
### <a name="sign-deployments-on-behalf-of-customer"></a>Implementaciones de inicio de sesión en nombre de cliente  
 Es una estrategia de implementación posibles para que el programador crear un mecanismo para firmar las implementaciones en nombre de sus clientes, mediante la clave privada del cliente. Esto evita que el desarrollador de tener que administrar claves privadas o varios paquetes de implementación. El desarrollador solo proporciona la misma implementación a cada cliente. Es responsabilidad del cliente personalizarla en función de su entorno mediante el servicio de firmado.  
  
 Un inconveniente de este método es el tiempo y el gasto necesarios para implementarla. Aunque este tipo de servicio se puede crear mediante el uso de las herramientas proporcionadas en .NET Framework SDK, agregará más tiempo de desarrollo para el ciclo de vida del producto.  
  
 Como se indicó anteriormente en este tema, otro inconveniente es que la versión de cada cliente de la aplicación tendrá la misma identidad de aplicación, que podría provocar conflictos. Si se trata de un problema, el desarrollador puede cambiar el campo de nombre que se utiliza al generar el manifiesto de implementación para proporcionar un nombre único a cada aplicación. Esto creará una identidad diferente para cada versión de la aplicación y eliminar cualquier posible conflicto de identidad. Este campo se corresponde con el `-Name` argumentos de Mage.exe y a la **nombre** campo el **nombre** ficha en MageUI.exe.  
  
 Por ejemplo, supongamos que el desarrollador ha creado una aplicación denominada Aplicación1. En lugar de crear una sola implementación con el campo de nombre establecido en Aplicación1, el programador puede crear varias implementaciones con una variación específica del cliente en este nombre, por ejemplo, Aplicación1-clientea, Aplicación1-ClienteB y así sucesivamente.  
  
### <a name="deploy-using-a-setup-package"></a>La implementación con un paquete de instalación  
 Una segunda estrategia de implementación posible consiste en generar un proyecto de Microsoft Setup para llevar a cabo la implementación inicial de la aplicación ClickOnce. Esto puede proporcionar en uno de los distintos formatos diferentes: como una implementación de MSI, que un programa de instalación ejecutable (. (EXE), o como un archivo contenedor (.cab) junto con un script por lotes.  
  
 Con esta técnica, el programador podría proporcionar al cliente una implementación que incluya los archivos de aplicación, el manifiesto de aplicación y un manifiesto de implementación que actúa como una plantilla. El cliente ejecute el programa de instalación que se pedirá de una dirección URL de implementación (el servidor o la ubicación desde la que los usuarios instalarán la aplicación de ClickOnce del recurso compartido de archivo), así como un certificado digital. También puede elegir la aplicación de instalación solicitar opciones de configuración de ClickOnce adicionales, como el intervalo de comprobación de actualización. Una vez que esta información se recopila, el programa de instalación debería generar el manifiesto de implementación real, firmarlo y publicar la aplicación ClickOnce en la ubicación del servidor designado.  
  
 Hay tres maneras de que el cliente pueda firmar el manifiesto de implementación en esta situación:  
  
1.  El cliente puede usar un certificado válido emitido por una entidad de certificación (CA).  
  
2.  Como una variante de este enfoque, puede elegir el cliente firmar el manifiesto de implementación con un certificado autofirmado. El inconveniente de esto es que hará que la aplicación mostrar las palabras "Editor desconocido" cuando el usuario se le pregunte si desea instalarlo. Sin embargo, la ventaja es que se evita que a los clientes menores de tener que dedicar tiempo y dinero necesarios para obtener un certificado emitido por una entidad de certificación.  
  
3.  Por último, el programador puede incluir su propio certificado autofirmado en el paquete de instalación. Esto presenta los posibles problemas con la identidad de aplicación mencionados anteriormente en este tema.  
  
 La desventaja para el método de proyecto de implementación de instalación es el tiempo y el gasto necesarios para compilar una aplicación de implementación personalizada.  
  
### <a name="have-customer-generate-deployment-manifest"></a>Hacer que el cliente genere manifiesto de implementación  
 Una tercera estrategia de implementación posibles es transferir sólo los archivos de aplicación y el manifiesto de aplicación desactivar al cliente. En este escenario, el cliente es responsable de utilizar .NET Framework SDK para generar y firmar el manifiesto de implementación.  
  
 El inconveniente de este método es que requiere el cliente para instalar las herramientas de .NET Framework SDK y para que un desarrollador o administrador del sistema con experiencia en su uso. Algunos clientes pueden exigir una solución que requiera poco o ningún esfuerzo técnico por su parte.  
  
## <a name="see-also"></a>Vea también  
 [Implementar aplicaciones ClickOnce para las pruebas y los servidores de producción sin nueva firma](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md)   
 [Tutorial: Implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Tutorial: Implementar manualmente una aplicación ClickOnce que no requiera el proceso de volver a firmar y que conserve la información de marca comercial](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)