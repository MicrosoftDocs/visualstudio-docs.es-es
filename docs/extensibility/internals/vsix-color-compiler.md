---
title: Compilador de Color VSIX | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 115f3a6c9d01d1e92a5eb7c840dfb17abcfd3c72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-color-compiler"></a>Compilador de Color VSIX
La herramienta de compilador de Color de extensión de Visual Studio es una aplicación de consola que toma un archivo .xml que representa los colores de los temas de Visual Studio existentes y convierte a un .pkgdef archivos para que los colores se pueden utilizar en Visual Studio. Dado que es más fácil comparar las diferencias entre los archivos .xml, esta herramienta es útil para administrar los colores personalizados en el control de código fuente. También puede enlazar con entornos de compilación para que el resultado de la compilación es un archivo .pkgdef válido.  
  
 **Esquema XML de tema**  
  
 Un archivo .xml de tema completo tiene el siguiente aspecto:  
  
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
  
 El \<tema > elemento define un tema completo. Un tema debe contener al menos un \<categoría > elemento. Elementos del tema se definen como el siguiente:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Attribute**|**Definición**|  
|nombre|[Required] El nombre del tema|  
|GUID|[Required] GUID del tema (deben coincidir con formato de GUID)|  
  
 Al crear colores personalizados para Visual Studio, los colores deben definirse para los temas siguientes. Si no existe ningún color para un tema determinado, Visual Studio intenta cargar los colores que faltan desde el tema claro.  
  
|||  
|-|-|  
|**Nombre del tema**|**GUID de tema**|  
|Claro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Oscuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Azul|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Contraste alto|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Categoría**  
  
 El \<categoría > elemento define una colección de colores en un tema. Nombres de categoría proporcionan agrupaciones lógicas y deben definirse como sigan como sea posible. Una categoría debe contener al menos un \<Color > elemento. Elementos de categoría se definen como el siguiente:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Attribute**|**Definición**|  
|nombre|[Required] El nombre de la categoría|  
|GUID|[Required] GUID de la categoría (deben coincidir con formato de GUID)|  
  
 **Color**  
  
 El \<Color > elemento define un color para un componente o el estado de la interfaz de usuario. El esquema de nomenclatura preferido para un color es [tipo de interfaz de usuario] [State]. No utilice la palabra "color", ya que es redundante. Un color debe indicar claramente el tipo de elemento y las situaciones o "state", para el que se aplicará el color. Un color no debe estar vacío y debe contener uno o ambos de un \<fondo > y \<primer plano > elemento. Elementos de color se definen como el siguiente:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Attribute**|**Definición**|  
|nombre|[Required] El nombre del color|  
  
 **Primer plano o fondo**  
  
 El \<fondo > y \<primer plano > elementos definen valor y el tipo para el primer plano de un elemento de interfaz de usuario o de fondo de un color. Estos elementos no tienen ningún elemento secundario.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Attribute**|**Definición**|  
|Tipo|[Required] El tipo del color. Puede ser uno de los siguientes:<br /><br /> *CT_INVALID:* el color no es válida o no.<br /><br /> *CT_RAW:* un valor ARGB sin formato.<br /><br /> *CT_COLORINDEX:* NO UTILICE.<br /><br /> *CT_SYSCOLOR:* un color de sistema de Windows en SysColor.<br /><br /> *CT_VSCOLOR:* un color de Visual Studio en __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* el color automático.<br /><br /> *CT_TRACK_FOREGROUND:* NO UTILICE.<br /><br /> *CT_TRACK_BACKGROUND:* NO UTILICE.|  
|Origen|[Required] El valor del color representado en formato hexadecimal|  
  
 Todos los valores admitidos por la enumeración __VSCOLORTYPE son compatibles con el esquema en el atributo de tipo. Sin embargo, se recomienda que use solo CT_RAW y CT_SYSCOLOR.  
  
 **Todos juntos**  
  
 Se trata de un ejemplo sencillo de un archivo .xml de tema válido:  
  
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
  
 VsixColorCompiler \<archivo XML > \<archivo PkgDef > \<Args opcional >  
  
 **Argumentos**  
  
||||  
|-|-|-|  
|**Nombre del conmutador**|**Notas**|**Obligatorio u opcional**|  
|Sin nombre (archivo .xml)|Esto es el primer parámetro sin nombre y es la ruta de acceso del archivo XML que se convertirá.|Obligatorio|  
|Sin nombre (archivo .pkgdef)|Esto es el segundo parámetro sin nombre y la ruta de acceso de salida para el archivo .pkgdef generado.<br /><br /> Valor predeterminado: \<nombre del archivo XML > .pkgdef|Optional|  
|/noLogo|Al establecer este indicador detiene la información de producto y de copyright de impresión.|Optional|  
|/?|Imprimir la información de ayuda.|Optional|  
|/help|Imprimir la información de ayuda.|Optional|  
  
 **Ejemplos**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   / Nologo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Notas  
  
-   Esta herramienta requiere que esté instalado la última versión de tiempo de ejecución de VC ++.  
  
-   Se admite únicamente un solo archivo. No se admite la conversión de forma masiva a través de las rutas de acceso de carpeta.  
  
## <a name="sample-output"></a>Resultados de ejemplo  
 El archivo .pkgdef generado por la herramienta será similar a la siguiente claves:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```