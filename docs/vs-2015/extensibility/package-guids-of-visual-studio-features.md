---
title: Empaquetar los GUID de características de Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C package GUIDs
ms.assetid: f56f0356-f3ac-48bc-9674-94259e29a4df
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8601b4f072c206ab19fdcb4a7248e79784af934a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546818"
---
# <a name="package-guids-of-visual-studio-features"></a>GUID del paquete de características de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar el siguientes GUID en el archivo .pkgundef de la aplicación de shell aislado excluir paquetes específicos de la aplicación.

## <a name="package-guids"></a>GUID del paquete

|Área de características|Nombre del paquete sin formato|GUID del paquete|
|------------------|----------------------|------------------|
|Core IDE|Paquete de deshacer|{1D76B2E0-F11B-11D2-AFC3-00105A9991EF}|
||Paquete del entorno de Visual Studio|{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}|
||Paquete de definición de comandos de Visual Studio|{44E07B02-29A5-11D3-B882-00C04F79F802}|
||Paquete de listado de directorio de Visual Studio|{5010C52F-44AB-4051-8CE1-D36C20D989B4}|
||Paquete comunes de IDE de Visual Studio|{6E87CFAD-6C05-4ADF-9CD7-3B7943875B7C}|
||Paquete de menú del entorno de Visual Studio|{715F10EB-9E99-11D2-BFC2-00C04F990235}|
||Paquete de administrador de bibliotecas de Visual Studio COM +|{ED8979BC-B02F-4dA9-A667-D3256C36220A}|
||Paquete de integración de Control de código fuente de Visual Studio|{53544C4D-E3F8-4AA0-8195-8A8D16019423}|
||Paquete de compilación de soluciones de Visual Studio|{282BD676-8B5B-11D0-8A34-00A0C91E2ACD}|
||Paquete de administración de texto|{F5E7E720-1401-11d1-883B-0000F87579D2}|
||Paquete de VsSettings de Visual Studio|{F74C5077-D848-4630-80C9-B00E68A1CA0C}|
|Help|Paquete de la Ayuda de Visual Studio|{4A791146-19E4-11D3-B86B-00C04F79F802}|
|Lista de tareas, lista de errores|ErrorListPackage|{4A9B7E50-AA16-11D0-A8C5-00A0C921A4D2}|
|Esquema de clase|Paquete de esquema de clase|{21AF45B0-FFA5-11D0-G63F-00A0C922E851}|
|Instalador de controles de cuadro de herramientas|Paquete del instalador de controles de cuadro de herramientas|{2C298B35-07DA-45F1-96A3-BE55D91C8d7A}|
|Proyectos web|Microsoft.VisualStudio.Web|{349C5850-65DF-11DA-9384-00065B846F21}|
||Paquete de sistema de proyecto de Visual Web Developer|{39C9C826-8EF8-4079-8C95-428F5B1C323F}|
||Paquete de persistencia del proyecto de Visual Web Developer|{8FF02D1A-C177-4AC8-A62F-88FC6EA65F57}|
||Paquete de migración de Web de Visual Web Developer|{C1DAB116-2D63-493A-B970-10D7DD0B476E}|
||Paquete de Web de Visual Web Developer|{E7f851C8-6267-4794-B0FE-7BCAB6DACBB4}|
||Web de Visual Web Developer|{DC7F691A-91FC-4F7B-923E-FE829C3A18DC}|
|Editor de HTML|Paquete del Editor de HTML de Visual Studio|{1B437D20-F8FE-11D2-A6AE-00104BCC7269}|
||Paquete de Editor de código fuente HTML de Visual Web Developer|{BFCC0C3C-6F87-4285-A6C8-BB616061800D}|
|Editor CSS|Paquete de edición de CSS de Visual Studio|{A764E895-518D-11d2-9A89-00C04F79EFC3}|
|Editor XML|Paquete de Editor XML de Visual Studio|{87569308-4813-40A0-9CD0-D7A30838CA3F}|
|Explorador web|Paquete de explorador Web de Visual Studio|{E8B06F41-6D01-11D2-AA7D-00C04F990343}|
||Generador de proyectos de aplicación Web, para la vista en la funcionalidad de explorador|{349C5851-65DF-11DA-9384-00065B846F21}|
|Editor binario|Paquete de Editor binario de Visual Studio|{5B98C2C0-CD7B-11D0-92DF-00A0C9138C45}|
|Diseñador de Windows Forms|Paquete de hospedaje Diseñador de Windows Forms|{68939055-38E0-4D17-92CB-8909710D8178}|
||Paquete de diseñador de Windows Forms|{7494682B-37A0-11D2-A273-00C04F8EF4FF}|
||Paquete de recursos del Diseñador de Windows Forms|{7B5D447B-0B12-41EA-A84E-C822034422D4}|
||Paquete de configuración de aplicación de Windows Forms|{80C7728B-70A6-4528-8669-73E02D1B9C41}|
||Paquete del Diseñador de ElementHost|{7EAB3C71-59FF-4571-A5F3-643F255FC2E6}|
|Interfaz de usuario del depurador|Depurador de Visual Studio|{C9DD4A57-47FB-11D2-83E7-00C04F9902C1}|
|Herramientas para bases de datos|Paquete de Visual Database Tools|{220A4C17-7E7C-4663-BBCC-5E607C6543CD}|
||Diseñadores de herramientas de base de datos de Visual Studio|{EF828E39-70F5-4b8e-A3A0-4C0ECD28A69A}|
||Diseñadores de datos de Visual Studio|{D6C919AA-1217-41E2-a13B-9B92E1866305}|
||Paquete de datos de Visual Studio|{E1AA7737-69BE-43d0-A425-E3097651E192}|
||Paquete de extensibilidad del Diseñador de datos de Visual Studio|{A8F602E2-40CE-4dAF-AE82-A457A91728B9}|
||Paquete de diseñadores y exploradores de Visual Studio|{8D8529D3-625D-4496-8354-3DAD630ECC1B}|
||Diseñador de informes de Microsoft|{F3A96850-E2AE-4E00-9278-8FE23F225A0D}|
|En tiempo de ejecución DSL|CommonModelingPackage|{D1091694-EA72-4BDD-8918-78324CC25448}|
||Microsoft.VisualStudio.TextTemplating|{A9696DE6-E209-414D-BBEC-A0506fb0E924}|
|Soporte técnico de SourceSafe|Paquete de proveedor Visual SourceSafe|{AA8EB8CD-7A51-11D0-92C3-00A0C9138C45}|
||Paquete de código auxiliar del proveedor Visual SourceSafe|{53544C4D-B03D-4209-A7D0-D9DD13A4019B}|
|WPF Designer|WPFFlavor.WPFPackage|{B3BAE735-386C-4030-8329-EF48EEDA4036}|
||XamlDesignerPackage|{512be089-83ec-4cc6-8483-cf16565ae209}|
||XamlLanguagePackage|{2ef1ec52-c8bf-4fe0-8ece-ba9c0d5d1603}|
||XamlDiagnosticsPackage|{8291c340-36b8-4c91-8c40-cce75398ff75}|
|Fragmentos de código|Paquete de fragmentos de código de Visual Studio|{0B680757-2C29-4531-80FA-535A5178AA98}|
|Administrados son compatibles con el proyecto de lenguaje|Enumerador de componente de Visual Studio|{588205E0-66e0-11D3-8600-00C04F6123B3}|
||Configuración de Visual Studio y el paquete de los diseñadores del proyecto|{67909B06-91E9-4F3E-AB50-495046BE9A9A}|
|Exportar plantilla...|Exportar paquete de plantillas|{F1E4CFCA-4573-4345-8718-7BDE2b1F0BE8}|

 Algunos paquetes nunca deben quitarse porque muchas otras características tienen dependencias en ellos. Por ejemplo, las que se indican en "Core IDE" nunca se deben quitar.

 Algunas características no se puede quitar por completo. Por ejemplo, no hay ningún paquete que se puede anular el registro para quitar **vista de clases** y sus menús asociados, las opciones y los servicios. El **vista de clases** ventana proporciona el paquete de entorno de Visual Studio, que también proporciona otras características claves del IDE. Si desea quitar **vista de clases**, también debe quitar **buscar y reemplazar**, el entorno **opciones** páginas, el **ventana de comandos**y el **salida** ventana.
