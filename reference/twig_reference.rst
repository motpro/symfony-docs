.. index::
    single: Symfony2 Twig 扩展

Symfony2 Twig 扩展
========================

Twig是Symfony2默认的模板引擎.单独来看,Tiwg已经包含了大量的内建函数,过滤器,标记跟测试(`http://twig.sensiolabs.org/documentation`_
滚动到页面底部可以看到参考列表)

Symfony2增加了很多定制的扩展在Twig上,以此合并一些组件到Twig模板中.
下面是关于所有定制函数,过滤器,标记和测试的信息,当你使用Symfony2
核心框架的时候就被加进Twig了.

可能也会有一些你在bundle中使用的标签,在这里没有被列举出来.

方法
---------

.. 当前版本新增的:: 2.2
    ``render`` 跟 ``controller``的方法是在在2.2才新增的,
     在这里``{% render %}`` 标记被使用而且有个不同的特征.

+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| 函数语法                                           | Usage                                                                                      |
+====================================================+============================================================================================+
| ``render(uri, options = {})``                      | 这个方法会通过所给的控制器或者URL来渲染一个片段                                            |
| ``render(controller('B:C:a', {params}))``          | 要知道更多详细信息, 请看 :ref:`templating-embedding-controller`.                           |
| ``render(path('route', {params}))``                |                                                                                            |
| ``render(url('route', {params}))``                 |                                                                                            |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``render_esi(controller('B:C:a', {params}))``      | 如果可以,这个方法会生成一个ESI标签 否则就退回到``Render渲染``行为                          |
| ``render_esi(url('route', {params}))``             | 要知道更多详细信息, 请看 :ref:`templating-embedding-controller`.                           |
| ``render_esi(path('route', {params}))``            |                                                                                            |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``render_hinclude(controller(...))``               | 这个方法会通过所给的控制器或者URL来生成一个包含标签                                        |
| ``render_hinclude(url('route', {params}))``        | 要知道更多详细信息, 请看 :ref:`templating-embedding-controller`.                           |
| ``render_hinclude(path('route', {params}))``       |                                                                                            |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``controller(attributes = {}, query = {})``        | 单独使用Render标签来提交到你想渲染的控制                                                   |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``asset(path, packageName = null)``                | 获得assets文件(js,css,image)的公开路径                                                     |
|                                                    | 要知道更多详细信息, 请看 ":ref:`book-templating-assets`".                                  |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``asset_version(packageName = null)``              | 获得包当前的版本                                                                           |
|                                                    | 要知道更多详细信息, 请看 ":ref:`book-templating-assets`".                                  |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``form(view, variables = {})``                     | 这个方法会渲染出一个完整表单的HTML代码,                                                    |
|                                                    | 更多相关信息在 :ref:`the Twig Form reference<reference-forms-twig-form>`.                  |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``form_start(view, variables = {})``               | 渲染一个form表单开始的HTML代码, more information in                                        |
|                                                    | in :ref:`the Twig Form reference<reference-forms-twig-start>`.                             |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``form_end(view, variables = {})``                 | 渲染一个form表单结束的HTML代码,连同所有的并没有没有渲染的字段                              |
|                                                    |                                                                                            |
|                                                    | 更多信息请看 :ref:`the Twig Form reference<reference-forms-twig-end>`.                     |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``form_enctype(view)``                             | 如果表单有 file 上传的input标签这个方法会渲染出必须的属性``enctype="multipart/form-data"``,|
|                                                    |                                                                                            |
|                                                    | 更多信息请看 :ref:`the Twig Form reference<reference-forms-twig-enctype>`.                 |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``form_widget(view, variables = {})``              | 这个方法会渲染出一个完整的表单或者一个特别的field的widget部件                              |
|                                                    | 更多信息请看 :ref:`the Twig Form reference<reference-forms-twig-widget>`.                  |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``form_errors(view)``                              | 这个方法会渲染出所给表单字段的错误信息或者全局的错误信息                                   |
|                                                    | 更多信息请看 :ref:`the Twig Form reference<reference-forms-twig-errors>`.                  |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``form_label(view, label = null, variables = {})`` | 这个方法会渲染出表单字段的label标签                                                        |
|                                                    | 更多信息请看 :ref:`the Twig Form reference<reference-forms-twig-label>`.                   |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``form_row(view, variables = {})``                 | This will render the row (the field's label, errors and widget) of the                     |
|                                                    | given field, 更多信息请看 in :ref:`the Twig Form reference<reference-forms-twig-row>`.     |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``form_rest(view, variables = {})``                | This will render all fields that have not yet been rendered,                               |
|                                                    | 更多信息请看 :ref:`the Twig Form reference<reference-forms-twig-rest>`.                    |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``csrf_token(intention)``                          | 这个方法会渲染一个csrf标记. 使用这个方法如果你想csrf保护但并不用自己再去创建一个csrf的表单 |
|                                                    |                                                                                            |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``is_granted(role, object = null, field = null)``  | 如果当前用户是所要求的角色(role) 则会返回 true,                                            |
|                                                    | 更多信息请看 ":ref:`book-security-template`"                                               |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``logout_path(key)``                               | 这个方法会通过所给的防火墙配置来生成的注销URL(相对路径)                                    |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``logout_url(key)``                                | 和``logout_path(...)``一样的方法,但是生成的是绝对路径的URL                                 |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``path(name, parameters = {})``                    | 通过所给路由来获得一个相对路径的URL,                                                       |
|                                                    | 更多信息请看 ":ref:`book-templating-pages`".                                               |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+
| ``url(name, parameters = {})``                     | 和``path(...)``一样,但是生成的是绝对路径的url                                              |
+----------------------------------------------------+--------------------------------------------------------------------------------------------+

过滤器
-------

+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| Filter Syntax                                                                   | Usage                                                             |
+=================================================================================+===================================================================+
| ``text|humanize``                                                               | Makes a technical name human readable (replaces underscores by    |
|                                                                                 | spaces and capitalizes the string)                                |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``text|trans(arguments = {}, domain = 'messages', locale = null)``              | This will translate the text into the current language, more      |
|                                                                                 | information in .                                                  |
|                                                                                 | :ref:`Translation Filters<book-translation-filters>`.             |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``text|transchoice(count, arguments = {}, domain = 'messages', locale = null)`` | This will translate the text with pluralization, more information |
|                                                                                 | in :ref:`Translation Filters<book-translation-filters>`.          |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``variable|yaml_encode(inline = 0)``                                            | This will transform the variable text into a YAML syntax.         |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``variable|yaml_dump``                                                          | This will render a yaml syntax with their type.                   |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``classname|abbr_class``                                                        | This will render an ``abbr`` element with the short name of a     |
|                                                                                 | PHP class.                                                        |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``methodname|abbr_method``                                                      | This will render a PHP method inside a ``abbr`` element           |
|                                                                                 | (e.g. ``Symfony\Component\HttpFoundation\Response::getContent``   |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``arguments|format_args``                                                       | This will render a string with the arguments of a function and    |
|                                                                                 | their types.                                                      |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``arguments|format_args_as_text``                                               | Equal to ``[...]|format_args``, but it strips the tags.           |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``path|file_excerpt(line)``                                                     | This will render an excerpt of a code file around the given line. |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``path|format_file(line, text = null)``                                         | This will render a file path in a link.                           |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``exceptionMessage|format_file_from_text``                                      | Equal to ``format_file`` except it parsed the default PHP error   |
|                                                                                 | string into a file path (i.e. 'in foo.php on line 45')            |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+
| ``path|file_link(line)``                                                        | This will render a path to the correct file (and line number)     |
+---------------------------------------------------------------------------------+-------------------------------------------------------------------+

Tags
----

+---------------------------------------------------+--------------------------------------------------------------------+
| Tag Syntax                                        | Usage                                                              |
+===================================================+====================================================================+
| ``{% form_theme form 'file' %}``                  | This will look inside the given file for overridden form blocks,   |
|                                                   | more information in :doc:`/cookbook/form/form_customization`.      |
+---------------------------------------------------+--------------------------------------------------------------------+
| ``{% trans with {variables} %}...{% endtrans %}`` | This will translate and render the text, more information in       |
|                                                   | :ref:`book-translation-tags`                                       |
+---------------------------------------------------+--------------------------------------------------------------------+
| ``{% transchoice count with {variables} %}``      | This will translate and render the text with pluralization, more   |
| ...                                               | information in :ref:`book-translation-tags`                        |
| ``{% endtranschoice %}``                          |                                                                    |
+---------------------------------------------------+--------------------------------------------------------------------+
| ``{% trans_default_domain language %}``           | This will set the default domain for message catalogues in the     |
|                                                   | current template                                                   |
+---------------------------------------------------+--------------------------------------------------------------------+

Tests
-----

+---------------------------------------------------+------------------------------------------------------------------------------+
| Test Syntax                                       | Usage                                                                        |
+===================================================+==============================================================================+
| ``selectedchoice(choice, selectedValue)``         | This will return ``true`` if the choice is selected for the given form value |
+---------------------------------------------------+------------------------------------------------------------------------------+

Global Variables
----------------

+-------------------------------------------------------+------------------------------------------------------------------------------------+
| Variable                                              | Usage                                                                              |
+=======================================================+====================================================================================+
| ``app`` *Attributes*: ``app.user``, ``app.request``   | The ``app`` variable is available everywhere, and gives you quick                  |
| ``app.session``, ``app.environment``, ``app.debug``   | access to many commonly needed objects. The ``app`` variable is                    |
| ``app.security``                                      | instance of :class:`Symfony\\Bundle\\FrameworkBundle\\Templating\\GlobalVariables` |
+-------------------------------------------------------+------------------------------------------------------------------------------------+

Symfony标准版扩展
-----------------------------------

Symfony标准版增添了一些bundle到Symfony2的核心框架

这些bundle可以有其它Twig扩展:

* **Twig Extension** includes all extensions that do not belong to the
  Twig core but can be interesting. You can read more in 
  `the official Twig Extensions documentation`_
* **Assetic** adds the ``{% stylesheets %}``, ``{% javascripts %}`` and 
  ``{% image %}`` tags. You can read more about them in 
  :doc:`the Assetic Documentation</cookbook/assetic/asset_management>`;
* **Translation** translated by mot . Weibo `http://weibo.com/mot99/` 2013-08-17

.. _`the official Twig Extensions documentation`: http://twig.sensiolabs.org/doc/extensions/index.html
.. _`http://twig.sensiolabs.org/documentation`: http://twig.sensiolabs.org/documentation

