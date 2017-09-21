---
title: "Crear una instalación sin conexión de Visual Studio 2017 RC | Microsoft Docs"
description: "Obtenga información sobre cómo crear una instalación sin conexión de Visual Studio."
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 33e765d205aa7ad8a3d8c5b871863ab659092a77
ms.lasthandoff: 02/22/2017

---
# <a name="create-an-offline-installation-of-visual-studio-2017-rc"></a>Crear una instalación sin conexión de Visual Studio 2017 RC

## <a name="create-a-layout"></a>Crear un diseño
Si quiere instalar [Visual Studio 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) en otro equipo que no tenga acceso a Internet, puede hacerlo creando primero un diseño de instalación sin conexión que contenga todos los archivos y componentes de Visual Studio que necesita.

Después, puede instalar Visual Studio en el equipo de destino con el diseño de instalación sin conexión que ha creado.     

> [!WARNING]
> Actualmente, el SDK de Android no admite una experiencia de instalación sin conexión. Si instala elementos de la instalación del SDK de Android en un equipo que no está conectado a Internet, es posible que se produzca un error en la instalación. Para obtener más información sobre esto, vaya a la sección [Solucionar los problemas de una instalación sin conexión](#tshootofflineinstall) de este tema.


#### <a name="to-create-an-offline-installation-layout-of-visual-studio"></a>Para crear un diseño de instalación sin conexión de Visual Studio
1. Descargue el archivo ejecutable de instalación de Visual Studio en una unidad de su equipo local.
  Por ejemplo, [descargue el archivo vs_enterprise.exe](https://www.visualstudio.com/vs/visual-studio-2017-rc/).
2. Ejecute `vs_enterprise.exe` con los siguientes argumentos (modificadores) desde un símbolo del sistema:

   a. Agregue `--layout <path>`, donde `<path>` es la ubicación en la que quiere que se descargue el diseño. Tenga en cuenta que las rutas de acceso relativas (por ejemplo, `..\vs2017`) no se admiten en este momento. De manera predeterminada, se descargan todos los idiomas. (Vea el ejemplo A).

   b. Restrinja la descarga a un subconjunto de los idiomas disponibles proporcionando el argumento `--lang <language>`, donde `<language>` es una o más de las configuraciones regionales de idioma.  (Vea el ejemplo B y el C).

   c. Restrinja la descarga a un subconjunto de cargas de trabajo y componentes proporcionando el argumento `--add <package ID>`. Esto descargará solo las cargas de trabajo y los componentes (y sus dependencias) que especifique. (Vea el ejemplo D y el E).

   Para obtener una lista completa de los id. de componente y carga de trabajo ordenados por producto de Visual Studio, vea nuestra página [Visual Studio 2017 Workload and Component IDs](https://aka.ms/vs2017componentids) (Identificadores de componente y carga de trabajo de Visual Studio 2017).

### <a name="examples"></a>Ejemplos
**Ejemplo A**: Descarga todas las cargas de trabajo y los componentes para todos los idiomas
  > ```vs_enterprise.exe --layout C:\vs2017```

**Ejemplo B**: Descarga todas las cargas de trabajo y los componentes para un idioma  
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US```

**Ejemplo C**: Descarga todas las cargas de trabajo y los componentes para varios idiomas
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US de-DE ja-JP```

**Ejemplo D**: Descarga una carga de trabajo para todos los idiomas
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure ```

**Ejemplo E**: Descarga dos cargas de trabajo y un componente opcional para tres idiomas
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```

  > [!WARNING]
  > El parámetro --layout producirá un error si el nombre de archivo .exe de instalación incluye números. Para evitar este problema, debe quitar los números del nombre de archivo; por ejemplo, cambie el nombre *vs_community__198521760.1486960229.exe* por ***vs_community.exe***.

### <a name="language-locales"></a>Configuraciones regionales de idioma

| Idioma-configuración regional | Lenguaje |
| -----   | ----- |
| cs-CZ    | Checo |
| de-DE    | Alemán |
| en-US    | Inglés |
| es-ES    | Español |
| fr-FR    | Francés |
| it-IT    | Italiano |
| ja-JP    | Japonés |
| ko-KR    | Coreano |
| pl-PL    | Polaco |
| pt-BR    | Portugués (Brasil) |
| ru-RU    | Ruso |
| tr-TR    | Turco |
| zh-CN    | Chino (simplificado) |
| zh-TW    | Chino (tradicional) |


## <a name="install-from-a-layout"></a>Instalar desde un diseño
#### <a name="to-install-visual-studio-from-an-offline-installation-layout"></a>Para instalar Visual Studio desde un diseño de instalación sin conexión
1. En el equipo de destino, vaya a la carpeta **Certificados**, que se encuentra en la carpeta Diseño.
2. Haga clic con el botón derecho e instale cada certificado en la carpeta **Certificados**.

  (Si se le pide una contraseña después de instalar un certificado, haga clic en **Continuar**).  
3. Ejecute `vs_enterprise.exe` desde la carpeta **Diseño**.

Nota: Si está instalando desde un diseño parcial y selecciona cargas de trabajo, componentes o idiomas que no están disponibles en el diseño, la configuración intentará descargarlos.  Si no tiene acceso a Internet, esos elementos no se podrán instalar.

> [!CAUTION]
> El diseño de instalación sin conexión crea actualmente algunos archivos con permisos restringidos (ACL) que impiden el acceso de todos los usuarios.  Asegúrese de que ajusta los permisos (ACL) de manera que concedan acceso de lectura a otros usuarios *antes* de que comparta la instalación sin conexión.

## <a name="update-an-installation-layout"></a>Actualizar un diseño de instalación
A medida que haya actualizaciones disponibles para Visual Studio 2017 RC, puede ejecutar el comando `--layout` de nuevo, que apunta a la misma carpeta de diseño, para asegurarse de que la carpeta contiene los últimos componentes. Solo se descargarán los componentes que se hayan actualizado desde la última vez que se ejecutó `--layout`.

## <a id="tshootofflineinstall"> </a>Solucionar los problemas de un diseño de instalación
Al instalar sin conexión desde la caché de instalación sin conexión, es posible que aparezcan mensajes de advertencia sobre la imposibilidad de instalar algunos componentes y paquetes. En la siguiente tabla se incluyen posibles soluciones para estos escenarios.

| Componente o paquete | Solución |
| -------------------- | -------- |
|Programa de instalación de Android SDK (nivel de API)| Debe tener una conexión a Internet para instalar paquetes de Android SDK (nivel de API). Si está en una red restringida, debe permitir el acceso a las siguientes direcciones URL cuando instale Visual Studio: <br><br> - http://dl.google.com:443 <br>- http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Para obtener información sobre cómo resolver posibles problemas con la configuración de proxy, vea la publicación del blog [Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Errores de instalación de Visual Studio [Instalación de Android SDK] detrás de un proxy).  |  

 > [!IMPORTANT]
 > A pesar de que, en general, se admite el uso de Visual Studio 2017 RC en un entorno de producción, las cargas de trabajo y los componentes que aparecen marcados como "Versión preliminar" en la interfaz de usuario de instalación no son compatibles para usarlos en un entorno de producción.

 ## <a name="see-also"></a>Vea también
 * [Instalar Visual Studio](install-visual-studio.md)
 * [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Notificar un problema con Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

