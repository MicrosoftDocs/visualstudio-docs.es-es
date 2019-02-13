---
title: Áreas de trabajo remotas para R
description: Describe cómo configurar áreas de trabajo remotas de R y conectarse a ellas desde Visual Studio.
ms.date: 12/04/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 9b31859d677ab69108ad5e2681890a8c4a88f854
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55911214"
---
# <a name="set-up-remote-workspaces"></a>Configurar áreas de trabajo remotas

En este artículo se explica cómo configurar un servidor remoto con SSL y un servicio de R adecuado. Esto permite a Herramientas de R para Visual Studio (RTVS) conectarse a un área de trabajo remota en ese servidor.

## <a name="remote-computer-requirements"></a>Requisitos del equipo remoto

- Windows 10, Windows Server 2016 o Windows Server 2012 R2. RTVS también necesita
- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) o superior

## <a name="install-an-ssl-certificate"></a>Instalar un certificado SSL

RTVS requiere que todas las comunicaciones con un servidor remoto se realicen a través de HTTP, lo que requiere un certificado SSL en el servidor. Puede usar un certificado firmado por una entidad de certificación de confianza (recomendado) o un certificado autofirmado. (Un certificado autofirmado hace que RTVS genere advertencias cuando se conecta). Con cualquiera de estas opciones, tiene que instalarlo en el equipo y permitir acceso a su clave privada.

### <a name="obtain-a-trusted-certificate"></a>Obtener un certificado de confianza

Una entidad de certificación emite el certificado de confianza (consulte [entidades de certificación en Wikipedia](https://en.wikipedia.org/wiki/Certificate_authority) para obtener información). Al igual que al obtener una tarjeta de identificación gubernamental, la emisión de un certificado de confianza implica más procesos y honorarios posibles, pero comprueba la autenticidad de la solicitud y del solicitante.

El campo clave que debe estar en el certificado es el nombre de dominio completo del equipo servidor de R. La entidad de certificación necesita pruebas de que tiene autorización para crear un servidor para el dominio al que pertenece el servidor.

Para obtener más información, consulte [certificados de clave pública](https://en.wikipedia.org/wiki/Public_key_certificate) en Wikipedia.

## <a name="install-an-ssl-certificate-on-windows"></a>Instalar un certificado SSL en Windows

El certificado SSL debe instalarse manualmente en Windows. Siga las instrucciones siguientes para instalar un certificado SSL.

### <a name="obtain-a-self-signed-certificate-windows"></a>Obtener un certificado autofirmado (Windows)

Omita esta sección si tiene un certificado de confianza. En comparación con un certificado de una entidad de confianza, un certificado autofirmado es como si crea usted mismo una tarjeta de identificación. Este proceso es, por supuesto, mucho más fácil que trabajar con una entidad de confianza, pero también carece de autenticación segura, lo que significa que un atacante puede sustituir con su propio certificado el certificado sin firmar y capturar todo el tráfico entre el cliente y el servidor. Por tanto, el *certificado autofirmado, debe usarse solo en escenarios de prueba, en una red de confianza y nunca en producción*.

Por este motivo, RTVS emite siempre la siguiente advertencia cuando se conecta a un servidor con un certificado autofirmado:

![Cuadro de diálogo de advertencia de certificado autofirmado](media/workspaces-remote-self-signed-certificate-warning.png)

Para emitir un certificado autofirmado:

1. Inicie sesión en el equipo servidor de R con una cuenta de administrador.
1. Abra un nuevo símbolo del sistema de PowerShell de administrador y emita el siguiente comando, reemplazando `"remote-machine-name"` con el nombre de dominio completo del equipo servidor.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Si nunca ha ejecutado PowerShell antes en el equipo servidor de R, ejecute el siguiente comando para habilitar la ejecución de comandos de forma explícita:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Para obtener información, vea [certificados autofirmados](https://en.wikipedia.org/wiki/Self-signed_certificate) en Wikipedia.

### <a name="install-the-certificate"></a>Instalar el certificado

Para instalar el certificado en el equipo remoto, ejecute *certlm.msc* (el administrador de certificados) desde un símbolo del sistema. Haga clic con el botón derecho en la carpeta **Personal** y seleccione el comando **Todas las tareas** > **Importar**:

![Comando de importación de certificado](media/workspaces-remote-certificate-import.png)

### <a name="grant-permissions-to-read-the-ssl-certificates-private-key"></a>Conceder permisos para leer la clave privada del certificado SSL

Una vez que se ha importado el certificado, conceda a la cuenta `NETWORK SERVICE` permisos para leer la clave privada, como se describe en las instrucciones siguientes. `NETWORK_SERVICE` es la cuenta usada para ejecutar el agente de R Services, que es el servicio que finaliza las conexiones SSL entrantes en el equipo servidor.

1. Ejecute *certlm.msc* (el administrador de certificados) desde un símbolo del sistema de administrador.
1. Expanda **Personal** > **Certificados**, haga clic con el botón derecho en el certificado y seleccione **Todas las tareas** > **Administrar claves privadas**.
1. Haga clic con el botón derecho en el certificado y seleccione el comando **Administrar claves privadas** en **Todas las tareas**.
1. En el cuadro de diálogo que aparece, seleccione **Agregar** y escriba `NETWORK SERVICE` como nombre de cuenta:

    ![Cuadro de diálogo Administrar claves privadas, agregando NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. Seleccione **Aceptar** dos veces para cerrar los cuadros de diálogo y confirmar los cambios.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Instalar un certificado SSL en Ubuntu

El paquete `rtvs-daemon` instalará un certificado autofirmado de forma predeterminada como parte de la instalación.

### <a name="obtain-a-self-signed-certificate-ubuntu"></a>Obtener un certificado autofirmado (Ubuntu)

Para conocer las ventajas y los riesgos de usar un certificado autofirmado, vea la descripción de Windows. El paquete `rtvs-daemon` genera y configura el certificado autofirmado durante la instalación. Tendrá que hacerlo solo si quiere reemplazar el certificado autofirmado generado de forma automática.

Para emitir un certificado autofirmado usted mismo:

1. Use SSH o inicie sesión en el equipo con Linux.
2. Instale el paquete `ssl-cert`:
    ```sh
    sudo apt-get install ssl-cert
    ```
3. Ejecute `make-ssl-cert` para generar el certificado SSL autofirmado predeterminado:
    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```
4. Convierta la clave y los archivos PEM generados a PFX. El archivo PFX generado debería estar en la carpeta principal:
    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configure-rtvs-daemon"></a>Configurar el demonio RTVS

La ruta de acceso al archivo de certificado SSL (la ruta de acceso a PFX) debe establecerse en */etc/rtvs/rtvsd.config.json*. Actualice `X509CertificateFile` y `X509CertificatePassword` con la ruta de acceso del archivo y la contraseña respectivamente.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

Guarde el archivo y reinicie el demonio, `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Instalar R Services en Windows

Para ejecutar código de R, el equipo remoto debe tener un intérprete de R instalado de la siguiente forma:

1. Descargue e instale uno de los siguientes programas:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R para Windows](https://cran.r-project.org/bin/windows/base/)

     Ambos tienen la misma funcionalidad, pero Microsoft R Open se beneficia de bibliotecas de álgebra lineal aceleradas de hardware cortesía de [Intel Math Kernel Library](https://software.intel.com/intel-mkl).

2. Ejecute el [instalador de R Services](https://aka.ms/rtvs-services) y reinicie el equipo cuando se le pida. El instalador realiza las siguientes acciones:

    - Cree una carpeta en *%PROGRAMFILES%\Herramientas de R para Visual Studio\1.0\\* y copie todos los archivos binarios necesarios.
    - Instala `RHostBrokerService` y `RUserProfileService` y los configura para que se inicien automáticamente.
    - Configura el servicio `seclogon` para que se inicie automáticamente.
    - Agregue *Microsoft.R.Host.exe* y *Microsoft.R.Host.Broker.exe* al firewall de reglas de entrada en el puerto predeterminado 5444.

R Services se inicia automáticamente cuando se reinicia el equipo:

- El **servicio de agente de host de R** controla todo el tráfico HTTPS entre Visual Studio y el proceso donde se ejecuta el código de R en el equipo.
- El **servicio de perfil de usuario de R** es un componente con privilegios que administra la creación de perfiles de usuario de Windows. Se llama al servicio cuando un nuevo usuario inicia sesión por primera vez en el equipo servidor de R.

Puede ver estos servicios en la consola de administración de servicios (*compmgmt.msc*).

## <a name="install-r-services-on-linux"></a>Instalar R Services en Linux

Para ejecutar código de R, el equipo remoto debe tener un intérprete de R instalado de la siguiente forma:

1. Descargue e instale uno de los siguientes programas:

   - [Microsoft R Open](https://mran.microsoft.com/open/)
   - [CRAN R para Windows](https://cran.r-project.org/bin/linux/ubuntu/)

     Ambos tienen la misma funcionalidad, pero Microsoft R Open se beneficia de bibliotecas de álgebra lineal aceleradas de hardware cortesía de [Intel Math Kernel Library](https://software.intel.com/intel-mkl).

2. Siga las instrucciones que aparecen en [Servicio R remoto para Linux](setting-up-remote-r-service-on-linux.md), que abarca equipos físicos Ubuntu, máquinas virtuales Ubuntu para Azure, subsistema de Windows para Linux (WSL) y contenedores Docker, incluso los que se ejecutan en Azure Container Repository.

## <a name="configure-r-services"></a>Configurar R Services

Con R Services en ejecución en el equipo remoto, también necesita crear cuentas de usuario, establecer reglas de firewall, configurar redes de Azure y configurar el certificado SSL.

1. Cuentas de usuario: Cree cuentas para cada usuario que acceda al equipo remoto. Puede crear cuentas de usuario locales estándar (sin privilegios), o puede unir el equipo servidor de R a su dominio y agregar los grupos de seguridad adecuados al grupo de seguridad `Users`.

1. Reglas de firewall: De forma predeterminada, el `R Host Broker` escucha en el puerto TCP 5444. Por lo tanto, asegúrese de que las reglas de firewall de Windows estén habilitadas para el tráfico entrante y saliente (el tráfico saliente se necesita para la instalación de paquetes y escenarios similares).  El instalador de R Services establece estas reglas automáticamente para el firewall de Windows integrado. En cambio, si usa un firewall de terceros, abra manualmente el puerto 5444 para `R Host Broker`.

1. Configuración de Azure: Si el equipo remoto es una máquina virtual en Azure, abra el puerto 5444 para el tráfico entrante en las redes de Azure también, que es independiente del firewall de Windows. Para obtener más información, consulte [Filtrado del tráfico de red con grupos de seguridad de red](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg) en la documentación de Azure.

1. Indique al agente de host de R qué certificado SSL debe cargar: Si está instalando el certificado en un servidor de intranet, es probable que el nombre de dominio completo del servidor sea el mismo que su nombre de NETBIOS. En este caso, no tiene que hacer nada, ya que este es el certificado predeterminado que se carga.

    En cambio, si está instalando el certificado en un servidor accesible desde Internet (por ejemplo, una máquina virtual de Azure), use el nombre de dominio completo (FQDN) del servidor, porque el FQDN de un servidor accesible desde Internet nunca es el mismo que su nombre de NETBIOS.

    Para usar el FQDN, vaya a donde está instalado R Services (*%PROGRAM FILES%\R Remote Service for Visual Studio\1.0* de forma predeterminada), abra el archivo *Microsoft.R.Host.Broker.Config.json* en un editor de texto y reemplace su contenido por el siguiente, asignando el nombre común al FQDN del servidor, como`foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Guarde el archivo y reinicie el equipo para aplicar los cambios.

## <a name="troubleshooting"></a>Solución de problemas

**P. El equipo servidor de R no responde, ¿qué puedo hacer?**

Intente hacer ping al equipo remoto desde la línea de comandos: `ping remote-machine-name`. Si al hacer ping se produce un error, asegúrese de que el equipo está en ejecución.

**P. La ventana interactiva de R indica que el equipo remoto está encendido, pero ¿por qué no se ejecuta el servicio?**

Existen tres razones posibles:

- [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) o superior no está instalado en el equipo.
- Las reglas de firewall `Microsoft.R.Host.Broker` y `Microsoft.R.Host` no están habilitadas para las conexiones entrantes y salientes en el puerto 5444.
- No se ha instalado ningún certificado SSL con `CN=<remote-machine-name>`.

Reinicie el equipo después de realizar cualquiera de los cambios anteriores. Después, asegúrese de que `RHostBrokerService` y `RUserProfileService` se ejecutan mediante el Administrador de tareas (pestaña Servicios) o *services.msc*.

**P. ¿Por qué indica la ventana interactiva de R "401 Acceso denegado" al conectarse con el servidor de R?**

Existen dos posibles motivos:

- Es muy probable que la cuenta `NETWORK SERVICE` no tenga acceso a la clave privada del certificado SSL. Siga las instrucciones anteriores para conceder acceso a `NETWORK SERVICE` a la clave privada.
- Asegúrese de que el servicio `seclogon` está en ejecución. Use *services.msc* para configurar `seclogon` para que se inicie automáticamente.

**P. ¿Por qué indica la ventana interactiva de R "404 No encontrado" al conectarse con el servidor de R?**

Probablemente, el error se deba a que faltan las bibliotecas redistribuibles de Visual C++. Compruebe la ventana interactiva de R para ver si hay un mensaje con respecto a que falte la biblioteca (DLL). Compruebe que está instalada la biblioteca redistribuible de VS 2015 y que tiene R también instalado.

**P. No tengo acceso a Internet o a un recurso desde la ventana interactiva de R, ¿qué puedo hacer?**

Asegúrese de que las reglas de firewall de `Microsoft.R.Host.Broker` y `Microsoft.R.Host` permiten el acceso saliente en el puerto 5444. Reinicie el equipo después de aplicar los cambios.

**P. He probado con todas estas soluciones, y aun así no funciona. ¿Ahora qué?**

Busque en los archivos de registro, en *C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp*. Esta carpeta contiene archivos de registro independientes para cada instancia ejecutada del servicio de agente de R. Se crea un archivo de registro cada vez que se reinicia el servicio. Consulte el archivo de registro más reciente para obtener pistas sobre lo que puede estar produciendo errores.
