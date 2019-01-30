---
title: Propiedades del enlazador de Clang (C++ para Android) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: jillfra
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 16dcb7ff5925f341fc78b57f1d9a4f011a27d576
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016803"
---
# <a name="clang-linker-properties-android-c"></a>Propiedades del enlazador de Clang (C++ para Android)

Propiedad. | Descripción | Opciones
--- | ---| ---
Archivo de salida | La opción invalida el nombre y la ubicación predeterminados del programa que crea el enlazador. (-o)
Mostrar progreso | Imprime los mensajes de progreso del enlazador.
Versión | La opción -version indica al enlazador que agregue un número de versión en el encabezado del ejecutable.
Habilitar resultado detallado | La opción -verbose indica al enlazador que genere mensajes detallados para la depuración.
Habilitar vinculación incremental | La opción indica al enlazador que habilite la vinculación incremental.
Ruta de búsqueda de biblioteca compartida | Permite que el usuario especifique la ruta de búsqueda de la biblioteca compartida.
Directorios de bibliotecas adicionales | Permite que el usuario invalide la ruta de acceso de la biblioteca del entorno. (Carpeta -L).
Informar de referencias de símbolos sin resolver | Al habilitar esta opción se informará de referencias de símbolos sin resolver.
Optimizar para uso de memoria | Se optimiza para el uso de memoria, ya que se vuelven a leer las tablas de símbolos cuando es necesario.
Omitir bibliotecas predeterminadas específicas | Especifica uno o más nombres de las bibliotecas predeterminadas que se ignorarán.
Forzar referencias de símbolos | Obliga a que los símbolos se especifiquen en el archivo de salida como no definidos.
Información del símbolo de depurador | Información del símbolo de depurador del archivo de salida. | **Incluir todos**<br>**Omitir símbolos innecesarios para el proceso de reubicación**<br>**Omitir solo información del símbolo del depurador**<br>**Omitir información de todos los símbolos**<br>
Información del símbolo del depurador de paquete | Quite la información de los símbolos del depurador antes de empaquetar.  Se usará una copia del binario original para la depuración.
Nombre de archivo de asignaciones | La opción Asignar indica al enlazador que cree un archivo de asignaciones con el nombre especificado por el usuario.
Marcar variables como de solo lectura después de la reubicación | Esta opción marca las variables como de solo lectura después de la reubicación.
Habilitar enlace de función inmediata | Esta opción marca el objeto para el enlace de función inmediata.
Requerir pila de ejecutable | Esta opción indica en la salida que no requiere una pila de ejecutable.
Archivo completo | El archivo completo usa todos los códigos de los orígenes y las dependencias adicionales.
Opciones adicionales | Opciones adicionales.
Dependencias adicionales | Especifica elementos adicionales que se agregarán a la línea de comandos del vínculo.
Dependencias de biblioteca | Esta opción permite especificar bibliotecas adicionales para agregarlas a la línea de comandos del vinculador. Las bibliotecas adicionales se agregarán al final de la línea de comandos del vinculador. Comienzan con *lib* y finalizan con la extensión *.a* o *.so*.  (-lFILE)
