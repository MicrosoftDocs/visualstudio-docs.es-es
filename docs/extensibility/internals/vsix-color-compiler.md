---
title: Compilador de color VSIX | Microsoft Docs
description: Obtenga información sobre la herramienta de compilador de color de extensión de Visual Studio, que es una aplicación de consola que describe los colores de los temas de Visual Studio en un archivo. pkgdef.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e6e4a07a023be398c4106984fe4dc33eddd2706
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929204"
---
# <a name="vsix-color-compiler"></a>Compilador de colores de VSIX
La herramienta de compilador de color de extensión de Visual Studio es una aplicación de consola que toma un archivo. XML que representa los colores de los temas existentes de Visual Studio y los incluye en un archivo. pkgdef para que esos colores se puedan usar en Visual Studio. Dado que es fácil comparar las diferencias entre los archivos. XML, esta herramienta es útil para administrar los colores personalizados en el control de código fuente. También se puede enlazar a entornos de compilación para que la salida de la compilación sea un archivo. pkgdef válido.

 **Esquema XML del tema**

 Un archivo Theme. XML completo tiene el siguiente aspecto:

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

 El \<Theme> elemento define un tema completo. Un tema debe contener al menos un \<Category> elemento. Los elementos de tema se definen de la siguiente manera:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Atributo**|**Definition**|
|-|-|
|Nombre|Desee Nombre del tema.|
|GUID|Desee GUID del tema (debe coincidir con el formato de GUID)|

 Al crear colores personalizados para Visual Studio, esos colores deben definirse para los temas siguientes. Si no existe ningún color para un tema determinado, Visual Studio intenta cargar los colores que faltan del tema claro.

|**Nombre del tema**|**GUID del tema**|
|-|-|
|Claro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Oscuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Azul|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Contraste alto|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Categoría**

 El \<Category> elemento define una colección de colores de un tema. Los nombres de categoría proporcionan agrupaciones lógicas y deben definirse de la manera más estrecha posible. Una categoría debe contener al menos un \<Color> elemento. Los elementos de la categoría se definen de la siguiente manera:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Atributo**|**Definition**|
|-|-|
|Nombre|Desee El nombre de la categoría.|
|GUID|Desee GUID de la categoría (debe coincidir con el formato de GUID)|

 **Color**

 El \<Color> elemento define un color para un componente o el estado de la interfaz de usuario. El esquema de nomenclatura preferido para un color es [UI type] [State]. No use la palabra "color", ya que es redundante. Un color debe indicar claramente el tipo de elemento y las situaciones, o "estado", para los que se aplicará el color. Un color no debe estar vacío y debe contener uno o ambos \<Background> \<Foreground> elementos y. Los elementos de color se definen de la siguiente manera:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Atributo**|**Definition**|
|-|-|
|Nombre|Desee Nombre del color.|

 **Fondo y/o primer plano**

 Los \<Background> \<Foreground> elementos y definen el valor y el tipo de un color para el fondo o el primer plano de un elemento de la interfaz de usuario. Estos elementos no tienen elementos secundarios.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Atributo**|**Definition**|
|-|-|
|Tipo|Desee Tipo del color. Puede tener uno de los valores siguientes:<br /><br /> *CT_INVALID:* El color no es válido o no está establecido.<br /><br /> *CT_RAW:* Valor ARGB sin formato.<br /><br /> *CT_COLORINDEX:* NO USE.<br /><br /> *CT_SYSCOLOR:* Un color del sistema Windows de SysColor.<br /><br /> *CT_VSCOLOR:* Un color de Visual Studio de __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* Color automático.<br /><br /> *CT_TRACK_FOREGROUND:* NO USE.<br /><br /> *CT_TRACK_BACKGROUND:* NO USE.|
|Source|Desee Valor del color representado en hexadecimal.|

 Todos los valores admitidos por la enumeración __VSCOLORTYPE son compatibles con el esquema en el atributo type. Sin embargo, se recomienda usar solo CT_RAW y CT_SYSCOLOR.

 **Todos juntos**

 Este es un ejemplo sencillo de un archivo Theme. xml válido:

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

## <a name="how-to-use-the-tool"></a>Cómo usar la herramienta
 **Sintaxis**

 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>

 **Argumentos**

|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|
|-|-|-|
|Sin nombre (archivo. xml)|Este es el primer parámetro sin nombre y es la ruta de acceso al archivo XML que se va a convertir.|Obligatorio|
|Sin nombre (archivo. pkgdef)|Este es el segundo parámetro sin nombre y es la ruta de acceso de salida para el archivo. pkgdef generado.<br /><br /> Valor predeterminado: \<XML Filename> . pkgdef|Opcional|
|/noLogo|Al establecer esta marca se detiene la impresión del producto y la información de copyright.|Opcional|
|/?|Imprime la información de ayuda.|Opcional|
|/help|Imprime la información de ayuda.|Opcional|

 **Ejemplos**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml/noLogo

## <a name="notes"></a>Notas

- Esta herramienta requiere que esté instalada la versión más reciente del motor en tiempo de ejecución de VC + +.

- Solo se admiten archivos individuales. No se admite la conversión masiva a través de rutas de acceso a carpetas.

## <a name="sample-output"></a>Salida de ejemplo
 El archivo. pkgdef generado por la herramienta será similar a las claves siguientes:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
