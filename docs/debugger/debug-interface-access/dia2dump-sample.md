---
title: Ejemplo Dia2dump | Microsoft Docs
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93c103387ff2acd7b041fc103bc519e9ac166593
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859651"
---
# <a name="dia2dump-sample"></a>Ejemplo Dia2dump

El ejemplo Dia2dump muestra cómo usar el Microsoft depurar interfaz acceso Software Development Kit (SDK de DIA) para consultar un archivo PDB para obtener información.

El ejemplo Dia2dump se instala con Visual Studio y contiene los archivos de solución y un origen. Se ejecuta el ejecutable compilado desde la línea de comandos. Puede mostrar el contenido de un archivo de base de datos (.pdb) de programa completo o sólo las secciones que le interesa.

## <a name="install-the-sample"></a>Instalar el ejemplo

El ejemplo se instala al elegir el **desarrollo de escritorio con C++** carga de trabajo en el instalador de Visual Studio. Para obtener información sobre cómo instalar Visual Studio y elija determinadas cargas de trabajo y componentes individuales, consulte [instalar Visual Studio](../../install/install-visual-studio.md).

Cuando se instala, el ejemplo está en el directorio de instalación de Visual Studio, en un subdirectorio denominado \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Compilar el ejemplo

De forma predeterminada, el directorio de instalación es un directorio protegido. Esto significa que debe usar un símbolo del sistema para desarrolladores con privilegios elevados o instancia de Visual Studio para crear y editar la solución de ejemplo en esta ubicación. Para simplificar la compilación, se recomienda en primer lugar copie los archivos desde el directorio de ejemplo en otro directorio, como una carpeta en la carpeta documentos y, a continuación, compile el ejemplo.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Para generar el ejemplo Dia2Dump en Visual Studio

1. Abra el archivo DIA2Dump.sln en Visual Studio. Si no copió la solución en otro directorio, se pedirá que reinicie Visual Studio con permisos elevados.

1. En **el Explorador de soluciones**, seleccione el proyecto de Dia2Dump (no la solución).

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](/cpp/ide/working-with-project-properties).

1. Abra el **propiedades de configuración** > **C o C++** > **General** página de propiedades.

1. En el **directorios de inclusión adicionales** propiedad, elija el control de lista desplegable y luego elija **editar**.

1. En el **directorios de inclusión adicionales** cuadro de diálogo, en el campo de edición, escriba el `$(VSInstallDir)DIA SDK\include` directory. Agregar este directorio para garantizar que el compilador puede encontrar el archivo dia2.h. Elija **Aceptar** para guardar los cambios.

1. Elija **Aceptar** para guardar los cambios en las propiedades del proyecto.

1. En el **compilar** menú, elija **recompilar solución**. De forma predeterminada, Visual Studio compila una versión de depuración de la muestra, ubicada en un subdirectorio de depuración del directorio de la solución.

1. Cierre Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Para generar el ejemplo Dia2Dump en la línea de comandos

1. En una ventana de símbolo del sistema para desarrolladores, cambie al directorio donde haya copiado los archivos de ejemplo. Si no los copió el ejemplo a otro directorio, debe usar un con privilegios elevados (ejecutar como administrador) ventana de símbolo del sistema para desarrolladores.

1. Escriba el comando `nmake makefile` para compilar la configuración de depuración predeterminada de dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Ejecutar el ejemplo Dia2Dump

Dia2Dump.exe se basa en el msdia*versión*.dll COM de servidor para proporcionar sus servicios. En Visual Studio 2015 y Visual Studio 2017, la versión es el archivo msdia140.dll. Si el msdia*versión*no se ha inicializado el servidor COM dll, debe registrarlo antes dia2dump.exe puede trabajar. El directorio del SDK de DIA tiene un subdirectorio bin que contiene el x86 versión del archivo DLL. Una versión para x64 máquinas de la arquitectura está en bin\amd64 y es una versión de ARM en bin\arm. Para registrar la dll, abra una ventana de símbolo del sistema para desarrolladores con privilegios elevados y cambie al directorio que contiene la versión de la arquitectura del equipo. Escriba el comando `regsvr32 msdia140.dll` para registrar el servidor COM.

### <a name="to-run-the-sample"></a>Para ejecutar el ejemplo

1. Abra un símbolo del sistema y cambie al directorio que contiene el dia2dump.exe que generó.

1. Escriba el comando `dia2dump filename` donde *filename* es el nombre de un archivo PDB para examinar. Si el archivo PDB está en otro directorio, utilice la ruta de acceso completa al archivo como *filename*. Este comando enumera todos los datos en el archivo PDB.

1. Dia2Dump tiene otras opciones para mostrar solamente la información seleccionada. Use el `dia2dump -?` comando para enumerar todas las opciones disponibles.

## <a name="see-also"></a>Vea también

- [Portar, migrar y actualizar proyectos de Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)  
