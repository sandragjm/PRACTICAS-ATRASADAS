# Ejercicios XPath

## Ejercicio 1. Librería
A partir del documento `libreria.xml` que se incluye en la tarea, genera las expresiones XPath para obtener la siguiente información:

1. Todos los autores del documento.

**Solución:**
```
//autor
```
**Resultado:**
```xml
<autor>Karlos Arguiñano</autor>
<autor>Carlos Montero</autor>
<autor>James McGovern</autor>
<autor>Per Bothner</autor>
<autor>Kurt Cagle</autor>
<autor>James Linn</autor>
<autor>Vaidyanathan Nagarajan</autor>
<autor>Erik T. Ray</autor>
```

2. Todos los títulos del documento.

**Solución:**
```
//titulo
```
**Resultado:**
```xml
<titulo idioma="es">1000 recetas de oro</titulo>
<titulo idioma="es">El desorden que dejas</titulo>
<titulo idioma="en">XQuery Kick Start</titulo>
<titulo>XML The foundation of XQuery</titulo>
<titulo>Understanding the XPath specification</titulo>
<titulo idioma="en">Learning XML</titulo>
<titulo>Introduction</titulo>
<titulo>Markup and Core Concepts</titulo>
```

3. Todos los títulos de un capítulo del documento.

**Solución:**
```
//capitulo/titulo
```
**Resultado:**
```xml
<titulo>XML The foundation of XQuery</titulo>
<titulo>Understanding the XPath specification</titulo>
<titulo>Introduction</titulo>
<titulo>Markup and Core Concepts</titulo>
```

4. Todos los títulos de un libro del documento.

**Solución:**
```
//libro/titulo
```
**Resultado:**
```xml
<titulo idioma="es">1000 recetas de oro</titulo>
<titulo idioma="es">El desorden que dejas</titulo>
<titulo idioma="en">XQuery Kick Start</titulo>
<titulo idioma="en">Learning XML</titulo>
```

5. Todos los elementos de un capítulo.

**Solución:**
```
//capitulo/*
```
**Resultado:**
```xml
<titulo>XML The foundation of XQuery</titulo>
<paginas>14</paginas>
<titulo>Understanding the XPath specification</titulo>
<paginas>35</paginas>
<titulo>Introduction</titulo>
<paginas>24</paginas>
<titulo>Markup and Core Concepts</titulo>
<paginas>34</paginas>
```

6. Todos los elementos de un capítulo en una sección.

**Solución:**
```
//seccion/capitulo/*
```
**Resultado:**
```xml
<titulo>XML The foundation of XQuery</titulo>
<paginas>14</paginas>
<titulo>Understanding the XPath specification</titulo>
<paginas>35</paginas>
```

7. Todos los elementos de un capítulo que no están en una sección.

**Solución:**
```
//capitulo[not(parent::seccion)]
```
**Resultado:**
```xml
<capitulo num="1">
  <titulo>Introduction</titulo>
  <paginas>24</paginas>
</capitulo>
<capitulo num="2">
  <titulo>Markup and Core Concepts</titulo>
  <paginas>34</paginas>
</capitulo>
```

8.   Títulos de libros que tienen un capítulo 1.


**Solución:**
```
//libro/titulo[..//capitulo/@num="1"]/node()
```
**Resultado:**
```xml
XQuery Kick Start
Learning XML
```

9.  Todos los atributos del hijo del último libro.


**Solución:**
```

```
**Resultado:**
```xml
idioma="en"
num="1"
num="2
```


10. El primer autor de cada libro.


**Solución:**
```
//libro/autor[1]
```
**Resultado:**
```xml
<autor>Karlos Arguiñano</autor>
<autor>Carlos Montero</autor>
<autor>James McGovern</autor>
<autor>Erik T. Ray</autor>
```

11. El tercer libro con toda su información.


**Solución:**
```
//libro[3]
```
**Resultado:**
```xml
<libro categoria="tecnología">
  <titulo idioma="en">XQuery Kick Start</titulo>
  <autor>James McGovern</autor>
  <autor>Per Bothner</autor>
  <autor>Kurt Cagle</autor>
  <autor>James Linn</autor>
  <autor>Vaidyanathan Nagarajan</autor>
  <seccion par="1">
    <capitulo num="1">
      <titulo>XML The foundation of XQuery</titulo>
      <paginas>14</paginas>
    </capitulo>
    <capitulo num="2">
      <titulo>Understanding the XPath specification</titulo>
      <paginas>35</paginas>
    </capitulo>
  </seccion>
  <anyo>2003</anyo>
  <precio>49.99</precio>
</libro>
```

12. Todos los elementos con atributos.


**Solución:**
```

```
**Resultado:**
```xml
<libro categoria="cocina">
  <titulo idioma="es">1000 recetas de oro</titulo>
  <autor>Karlos Arguiñano</autor>
  <anyo>2018</anyo>
  <precio>30.00</precio>
</libro>
<titulo idioma="es">1000 recetas de oro</titulo>
<libro categoria="novela">
  <titulo idioma="es">El desorden que dejas</titulo>
  <autor>Carlos Montero</autor>
  <anyo>2016</anyo>
  <precio>18.95</precio>
</libro>
<titulo idioma="es">El desorden que dejas</titulo>
<libro categoria="tecnología">
  <titulo idioma="en">XQuery Kick Start</titulo>
  <autor>James McGovern</autor>
  <autor>Per Bothner</autor>
  <autor>Kurt Cagle</autor>
  <autor>James Linn</autor>
  <autor>Vaidyanathan Nagarajan</autor>
  <seccion par="1">
    <capitulo num="1">
      <titulo>XML The foundation of XQuery</titulo>
      <paginas>14</paginas>
    </capitulo>
    <capitulo num="2">
      <titulo>Understanding the XPath specification</titulo>
      <paginas>35</paginas>
    </capitulo>
  </seccion>
  <anyo>2003</anyo>
  <precio>49.99</precio>
</libro>
<titulo idioma="en">XQuery Kick Start</titulo>
<seccion par="1">
  <capitulo num="1">
    <titulo>XML The foundation of XQuery</titulo>
    <paginas>14</paginas>
  </capitulo>
  <capitulo num="2">
    <titulo>Understanding the XPath specification</titulo>
    <paginas>35</paginas>
  </capitulo>
</seccion>
<capitulo num="1">
  <titulo>XML The foundation of XQuery</titulo>
  <paginas>14</paginas>
</capitulo>
<capitulo num="2">
  <titulo>Understanding the XPath specification</titulo>
  <paginas>35</paginas>
</capitulo>
<libro categoria="web" cubierta="tapa blanda">
  <titulo idioma="en">Learning XML</titulo>
  <autor>Erik T. Ray</autor>
  <capitulo num="1">
    <titulo>Introduction</titulo>
    <paginas>24</paginas>
  </capitulo>
  <capitulo num="2">
    <titulo>Markup and Core Concepts</titulo>
    <paginas>34</paginas>
  </capitulo>
  <anyo>2003</anyo>
  <precio>39.95</precio>
</libro>
<titulo idioma="en">Learning XML</titulo>
<capitulo num="1">
  <titulo>Introduction</titulo>
  <paginas>24</paginas>
</capitulo>
<capitulo num="2">
  <titulo>Markup and Core Concepts</titulo>
  <paginas>34</paginas>
</capitulo>
```


13. Todos los elementos con un atributo de idioma.

**Solución:**
```
//*[@idioma]
```
**Resultado:**
```xml
<titulo idioma="es">1000 recetas de oro</titulo>
<titulo idioma="es">El desorden que dejas</titulo>
<titulo idioma="en">XQuery Kick Start</titulo>
<titulo idioma="en">Learning XML</titulo>
```

14. Todos los atributos de categoría.

**Solución:**
```
@categoria
```
**Resultado:**
```xml
categoria="cocina"
categoria="novela"
categoria="tecnología"
categoria="web"
```

15. Libros sin atributo de cubierta.

**Solución:**
```
//libro[not(@cubierta)]
```
**Resultado:**
```xml
<libro categoria="cocina">
  <titulo idioma="es">1000 recetas de oro</titulo>
  <autor>Karlos Arguiñano</autor>
  <anyo>2018</anyo>
  <precio>30.00</precio>
</libro>
<libro categoria="novela">
  <titulo idioma="es">El desorden que dejas</titulo>
  <autor>Carlos Montero</autor>
  <anyo>2016</anyo>
  <precio>18.95</precio>
</libro>
<libro categoria="tecnología">
  <titulo idioma="en">XQuery Kick Start</titulo>
  <autor>James McGovern</autor>
  <autor>Per Bothner</autor>
  <autor>Kurt Cagle</autor>
  <autor>James Linn</autor>
  <autor>Vaidyanathan Nagarajan</autor>
  <seccion par="1">
    <capitulo num="1">
      <titulo>XML The foundation of XQuery</titulo>
      <paginas>14</paginas>
    </capitulo>
    <capitulo num="2">
      <titulo>Understanding the XPath specification</titulo>
      <paginas>35</paginas>
    </capitulo>
  </seccion>
  <anyo>2003</anyo>
  <precio>49.99</precio>
</libro>
```

16.  Elementos con más de 5 hijos.
    
**Solución:**
```
//*[count(child::*) > 5]
```
**Resultado:**
```xml
<libro categoria="tecnología">
  <titulo idioma="en">XQuery Kick Start</titulo>
  <autor>James McGovern</autor>
  <autor>Per Bothner</autor>
  <autor>Kurt Cagle</autor>
  <autor>James Linn</autor>
  <autor>Vaidyanathan Nagarajan</autor>
  <seccion par="1">
    <capitulo num="1">
      <titulo>XML The foundation of XQuery</titulo>
      <paginas>14</paginas>
    </capitulo>
    <capitulo num="2">
      <titulo>Understanding the XPath specification</titulo>
      <paginas>35</paginas>
    </capitulo>
  </seccion>
  <anyo>2003</anyo>
  <precio>49.99</precio>
</libro>
<libro categoria="web" cubierta="tapa blanda">
  <titulo idioma="en">Learning XML</titulo>
  <autor>Erik T. Ray</autor>
  <capitulo num="1">
    <titulo>Introduction</titulo>
    <paginas>24</paginas>
  </capitulo>
  <capitulo num="2">
    <titulo>Markup and Core Concepts</titulo>
    <paginas>34</paginas>
  </capitulo>
  <anyo>2003</anyo>
  <precio>39.95</precio>
</libro>
```

17. Título de los libros con más de un autor.

**Solución:**
```
//libro[count(autor) > 1]/titulo/node()
```
**Resultado:**
```xml
XQuery Kick Start
```

18. Nodos que comienzan con la letra 'a'.

**Solución:**
```
//*[starts-with(name(), "a")]
```
**Resultado:**
```xml
<autor>Karlos Arguiñano</autor>
<anyo>2018</anyo>
<autor>Carlos Montero</autor>
<anyo>2016</anyo>
<autor>James McGovern</autor>
<autor>Per Bothner</autor>
<autor>Kurt Cagle</autor>
<autor>James Linn</autor>
<autor>Vaidyanathan Nagarajan</autor>
<anyo>2003</anyo>
<autor>Erik T. Ray</autor>
<anyo>2003</anyo>
```

19. Los nodos hijos de libro que comienzan con la letra 'p'.

**Solución:**
```
//libro/*[starts-with(name(), "p")]
```
**Resultado:**
```xml
<precio>30.00</precio>
<precio>18.95</precio>
<precio>49.99</precio>
<precio>39.95</precio>
```

20. Nodos hijos de libro que contienen 'io'.
    
**Solución:**
```
//libro/*[contains(name(), "io")]
```
**Resultado:**
```xml
<precio>30.00</precio>
<precio>18.95</precio>
<seccion par="1">
  <capitulo num="1">
    <titulo>XML The foundation of XQuery</titulo>
    <paginas>14</paginas>
  </capitulo>
  <capitulo num="2">
    <titulo>Understanding the XPath specification</titulo>
    <paginas>35</paginas>
  </capitulo>
</seccion>
<precio>49.99</precio>
<precio>39.95</precio>
```

21. Atributos que contienen 'io' en su nombre.

**Solución:**
```

```
**Resultado:**
```xml
idioma="es"
idioma="es"
idioma="en"
idioma="en"
```

22.  Títulos escritos en español y posteriores a 2016.

**Solución:**
```
//libro[anyo > 2016]/titulo[@idioma = "es"]
```
**Resultado:**
```xml
<titulo idioma="es">1000 recetas de oro</titulo>
```

## Ejercicio 2. Factbook
A partir del documento `factbook.xml` que viene como ejemplo al instalar BaseX, genera las expresiones XPath para obtener la siguiente información:

1. Nombre de los continentes.

**Solución:**
```
//continent/@name/string()
```
**Resultado:**
```xml
Europe
Asia
America
Australia/Oceania
Africa
```

2. Nombre del río que ocupa la décima posición.

**Solución:**
```
//river[position()=10]/@name
```
**Resultado:**
```xml
name="Zambezi"
```

3. Nombre de la isla cuya superficie es 13935.

**Solución:**
```
//island[@area=13935]/@name
```
**Resultado:**
```xml
name="Bahamas"
```

4. Nombre de los países que no tienen frontera con otros países (por tanto, islas).

**Solución:**
```

```
**Resultado:**
```xml
name="Faroe Islands"
name="Guernsey"
name="Iceland"
(...)
name="Mayotte"
name="Sao Tome and Principe"
76 resultados
```

5. Nombre de organizaciones que tengan más de 5 miembros.

**Solución:**
```
//organization[count(members) > 5]/@name
```
**Resultado:**
```xml
name="African, Caribbean, and Pacific Countries"
name="African Development Bank"
name="Agency for Cultural and Technical Cooperation"
(...)
name="World Trade Organization"
name="Zangger Committee"
132 resultados
```

6. "Hermanos menores" de la provincia de nombre Madrid, descendiente del país Spain.

**Solución:**
```

```
**Resultado:**
```xml
17 resultados
```

7. Nombre y gobierno de los países cuya población sea menor que 1.000.000.

**Solución:**
```
//country[@population < 1000000]/(@name|@government)
```
**Resultado:**
```xml
name="Andorra"
government="     parliamentary democracy that retains as its heads of state a coprincipality"
name="Faroe Islands"
government="part of the Danish realm"
160 resultados
```

8. Nombre de los países que tengan una ciudad llamada Córdoba.

**Solución:**
```
//country/province/city[name="Cordoba"]/../../@name
```
**Resultado:**
```xml
name="Spain"
name="Argentina"
name="Mexico"
```

9.  Nombre de los lagos ubicados en Russia.

**Solución:**
```
//lake/located[@country=/mondial/country[@name="Russia"]/@id]/../@name
```
**Resultado:**
```xml
name="Ozero Ladoga"
name="Ozero Baikal"
name="Ozero Onega"
name="Ozero Taimyr"
name="Ozero Chanka"
name="Ozero Tschany"
```

10. Nombre de los países cuyo territorio está en Europe.

**Solución:**
```

```
**Resultado:**
```xml
name="Albania"
name="Andorra"
name="Austria"
51 resultados
```

