---
title: VsIX Color Compiler | Microsoft Docs
description: Obtenga información sobre la Visual Studio Extension Color Compiler, que es una aplicación de consola que cubre los colores de Visual Studio temas en un archivo .pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2f7277299d3cedd2ea0db49a44109d8a0441ebd0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901765"
---
# <a name="vsix-color-compiler"></a>Compilador de colores de VSIX
La herramienta compilador de colores de extensión de Visual Studio es una aplicación de consola que toma un archivo .xml que representa los colores de los temas de Visual Studio existentes y lo cubre en un archivo .pkgdef para que esos colores se puedan usar en Visual Studio. Dado que es fácil comparar las diferencias entre los archivos .xml, esta herramienta es útil para administrar colores personalizados en el control de código fuente. También se puede enlazar a entornos de compilación para que la salida de la compilación sea un archivo .pkgdef válido.

 **Esquema XML de tema**

 Un archivo de .xml completo tiene este aspecto:

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **Tema**

 El \<Theme> elemento define un tema completo. Un tema debe contener al menos un \<Category> elemento. Los elementos de tema se definen de esta forma:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Atributo**|**Definición**|
|-|-|
|Nombre|[Obligatorio] Nombre del tema|
|GUID|[Obligatorio] GUID del tema (debe coincidir con el formato GUID)|

 Al crear colores personalizados para Visual Studio, esos colores deben definirse para los temas siguientes. Si no hay colores para un tema determinado, Visual Studio cargar los colores que faltan desde el tema Claro.

|**Nombre del tema**|**GUID de tema**|
|-|-|
|Claro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Oscuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Azul|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Contraste alto|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Categoría**

 El \<Category> elemento define una colección de colores en un tema. Los nombres de categoría proporcionan agrupaciones lógicas y deben definirse lo más estrechamente posible. Una categoría debe contener al menos un \<Color> elemento. Los elementos de categoría se definen de esta forma:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Atributo**|**Definición**|
|-|-|
|Nombre|[Obligatorio] Nombre de la categoría|
|GUID|[Obligatorio] GUID de la categoría (debe coincidir con el formato GUID)|

 **Color**

 El \<Color> elemento define un color para un componente o estado de la interfaz de usuario. El esquema de nomenclatura preferido para un color es [tipo de interfaz de usuario] [Estado]. No use la palabra "color", ya que es redundante. Un color debe indicar claramente el tipo de elemento y las situaciones, o "estado", a las que se aplicará el color. Un color no debe estar vacío y debe contener uno o ambos de un \<Background> elemento \<Foreground> y . Los elementos de color se definen de esta forma:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Atributo**|**Definición**|
|-|-|
|Nombre|[Obligatorio] Nombre del color|

 **Fondo o primer plano**

 Los elementos y definen el valor y el tipo de \<Background> un color para el fondo o el primer plano de un elemento de la interfaz de \<Foreground> usuario. Estos elementos no tienen elementos secundarios.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Atributo**|**Definición**|
|-|-|
|Tipo|[Obligatorio] Tipo del color. Puede tener uno de los valores siguientes:<br /><br /> *CT_INVALID:* El color no es válido o no está establecido.<br /><br /> *CT_RAW:* Valor ARGB sin formato.<br /><br /> *CT_COLORINDEX:* NO USE.<br /><br /> *CT_SYSCOLOR:* Color del sistema de Windows de SysColor.<br /><br /> *CT_VSCOLOR:* Color Visual Studio de __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Color automático.<br /><br /> *CT_TRACK_FOREGROUND:* NO USE.<br /><br /> *CT_TRACK_BACKGROUND:* NO USE.|
|Origen|[Obligatorio] Valor del color representado en hexadecimal|

 Todos los valores admitidos por la enumeración __VSCOLORTYPE son compatibles con el esquema en el atributo Type. Sin embargo, se recomienda usar solo CT_RAW y CT_SYSCOLOR.

 **Todos juntos**

 Este es un ejemplo sencillo de un tema válido .xml archivo:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>Uso de la herramienta
 **Sintaxis**

 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>

 **Argumentos**

|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|
|-|-|-|
|Sin nombre (.xml archivo)|Este es el primer parámetro sin nombre y es la ruta de acceso al archivo XML que se va a convertir.|Obligatorio|
|Sin nombre (archivo .pkgdef)|Este es el segundo parámetro sin nombre y es la ruta de acceso de salida para el archivo .pkgdef generado.<br /><br /> Valor predeterminado: \<XML Filename> .pkgdef|Opcionales|
|/noLogo|Al establecer esta marca, se impide que se imprima la información del producto y de los derechos de autor.|Opcionales|
|/?|Imprimir información de ayuda.|Opcionales|
|/help|Imprimir información de ayuda.|Opcional|

 **Ejemplos**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml /noLogo

## <a name="notes"></a>Notas

- Esta herramienta requiere que se instale la versión más reciente del entorno de ejecución de VC++.

- Solo se admiten archivos individuales. No se admite la conversión masiva a través de rutas de acceso de carpeta.

- La herramienta se puede encontrar en `<VS Install Path>\VSSDK\VisualStudioIntegration\Tools\Bin\`

## <a name="sample-output"></a>Salida de ejemplo
 El archivo .pkgdef generado por la herramienta será similar a las claves siguientes:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
