---
title: Compilador de colores VSIX (VSIX Color Compiler) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703901"
---
# <a name="vsix-color-compiler"></a>Compilador de colores de VSIX
La herramienta Visual Studio Extension Color Compiler es una aplicación de consola que toma un archivo .xml que representa colores para los temas de Visual Studio existentes y lo encubre en un archivo .pkgdef para que esos colores se puedan usar en Visual Studio. Dado que es fácil comparar las diferencias entre los archivos .xml, esta herramienta es útil para administrar colores personalizados en el control de código fuente. También se puede enlazar a entornos de compilación para que la salida de la compilación sea un archivo .pkgdef válido.

 **Esquema XML de tema**

 Un archivo .xml de tema completo tiene este aspecto:

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

 El \<elemento Theme> define un tema completo. Un tema debe contener \<al menos un elemento de categoría>. Los elementos temáticos se definen así:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**Atributo**|**Definición**|
|Nombre|[Requerido] El nombre del tema|
|GUID|[Requerido] GUID del tema (debe coincidir con el formato GUID)|

 Al crear colores personalizados para Visual Studio, esos colores deben definirse para los siguientes temas. Si no existen colores para un tema determinado, Visual Studio intenta cargar los colores que faltan desde el tema Luz.

|||
|-|-|
|**Nombre del tema**|**GUID temático**|
|Ligero|•de3dbbcd-f642-433c-8353-8f1df4370aba|
|Oscuro|N.o 1ded0138-47ce-435e-84ef-9ec1f439b749?|
|Azul|.a4d6a176-b948-4b29-8c66-53c97a1ed7d0|
|Contraste alto|.a4d6a176-b948-4b29-8c66-53c97a1ed7d0|

 **Categoría**

 El \<elemento Category> define una colección de colores en un tema. Los nombres de categoría proporcionan agrupaciones lógicas y deben definirse de la forma más estrecha posible. Una categoría debe contener \<al menos un elemento Color>. Los elementos de categoría se definen así:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**Atributo**|**Definición**|
|Nombre|[Requerido] El nombre de la categoría|
|GUID|[Requerido] GUID de la categoría (debe coincidir con el formato GUID)|

 **Color**

 El \<elemento Color> define un color para un componente o estado de la interfaz de usuario. El esquema de nomenclatura preferido para un color es [Tipo de interfaz de usuario] [Estado]. No utilice la palabra "color", ya que es redundante. Un color debe indicar claramente el tipo de elemento y las situaciones, o "estado", para las que se aplicará el color. Un color no debe estar vacío y debe \<contener uno \<o ambos de un elemento de fondo> y> de primer plano. Los elementos de color se definen así:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**Atributo**|**Definición**|
|Nombre|[Requerido] El nombre del color|

 **Antecedentes y/o Primer plano**

 Los \<elementos \<de> de fondo y> de primer plano definen el valor y el tipo de un color para el fondo o el primer plano de un elemento de interfaz de usuario. Estos elementos no tienen hijos.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**Atributo**|**Definición**|
|Tipo|[Requerido] El tipo del color. Puede tener uno de los valores siguientes:<br /><br /> *CT_INVALID:* El color no es válido o no está establecido.<br /><br /> *CT_RAW:* Un valor ARGB sin procesar.<br /><br /> *CT_COLORINDEX:* NO USAR.<br /><br /> *CT_SYSCOLOR:* Un color del sistema Windows de SysColor.<br /><br /> *CT_VSCOLOR:* Un color de Visual Studio de __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* El color automático.<br /><br /> *CT_TRACK_FOREGROUND:* NO USAR.<br /><br /> *CT_TRACK_BACKGROUND:* NO USAR.|
|Source|[Requerido] El valor del color representado en hexadecimal|

 Todos los valores admitidos por la enumeración __VSCOLORTYPE son compatibles con el esquema en el Type atributo. Sin embargo, le recomendamos que utilice solo CT_RAW y CT_SYSCOLOR.

 **Todos juntos**

 Este es un ejemplo sencillo de un archivo .xml de tema válido:

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

## <a name="how-to-use-the-tool"></a>Cómo utilizar la herramienta
 **Sintaxis**

 El archivo \<XML VsixColorCompiler \<> \<archivo PkgDef>> Args opcionales

 **Argumentos**

||||
|-|-|-|
|**Cambiar nombre**|**Notas**|**Requerido u Opcional**|
|Sin nombre (archivo .xml)|Este es el primer parámetro sin nombre y es la ruta de acceso al archivo XML que se va a convertir.|Obligatorio|
|Sin nombre (archivo .pkgdef)|Este es el segundo parámetro sin nombre y es la ruta de salida para el archivo .pkgdef generado.<br /><br /> Predeterminado: \<Nombre de archivo XML>.pkgdef|Opcional|
|/noLogo|Al establecer esta marca, se detiene la impresión de la información del producto y de los derechos de autor.|Opcional|
|/?|Imprima la información de ayuda.|Opcional|
|/help|Imprima la información de ayuda.|Opcional|

 **Ejemplos**

- VsixColorCompiler D:-xml-colors.xml D:-pkgdef-colors.pkgdef

- VsixColorCompiler D:-xml-colors.xml /noLogo

## <a name="notes"></a>Notas

- Esta herramienta requiere que se instale la última versión del tiempo de ejecución VC++.

- Solo se admiten archivos individuales. No se admite la conversión masiva a través de rutas de carpeta.

## <a name="sample-output"></a>Salida de ejemplo
 El archivo .pkgdef generado por la herramienta será similar a las siguientes claves:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
