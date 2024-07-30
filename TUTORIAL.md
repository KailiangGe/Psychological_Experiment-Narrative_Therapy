# 心理学实验程序教程
# 目录

### 开始：介绍jspsych
### 第一步：设置HTML页面结构
### 第二步：引入jsPsych库
### 第三步：初始化jsPsych ##
### 第四步：创建欢迎界面 ##
### 第五步：创建前测问卷 ##
### 第六步：创建叙事疗法引导页面 ##
### 第七步：创建叙事疗法任务 ##
### 第八步：创建后测问卷和结束界面 ##
### 完整的.html文件代码 ##
### 用CSS添加样式 ###

# 正文
## 开始：介绍jspsych

### 1.什么是 jsPsych？

`jsPsych` 是一个 JavaScript 库，专门用于创建和管理在线心理学实验。它提供了一套全面的工具和插件，使得研究人员可以方便地设计复杂的心理学实验，并且在网页上运行这些实验。`jsPsych` 支持多种实验设计，包括反应时间测量、调查问卷、视觉和听觉刺激展示等。

### 2.jsPsych 的主要功能

- **灵活的实验设计**：允许用户创建各种类型的实验任务，包括调查问卷、反应时间任务和多媒体刺激任务。
- **插件系统**：提供了许多插件来处理不同类型的任务，如文本调查、图片展示、键盘响应等。用户还可以自定义插件以满足特定需求。
- **数据收集和分析**：内置的数据收集功能，可以将实验数据保存为 JSON 格式，便于后续分析。
- **兼容性**：支持在大多数现代浏览器中运行，包括桌面和移动设备。

### 3.优点

1. **易于使用**：`jsPsych` 提供了高层次的抽象，使得实验设计更加简单。即使没有深厚的编程背景，用户也可以快速上手。
2. **开源和免费**：`jsPsych` 是一个开源项目，用户可以自由使用和修改源码，同时享受社区支持。
3. **文档和社区支持**：提供了详细的文档和示例代码，社区也非常活跃，有助于解决在使用过程中遇到的问题。
4. **高度可定制**：用户可以根据实验需要自定义插件，或编写自己的插件来扩展 `jsPsych` 的功能。

### 4.缺点

1. **学习曲线**：虽然基础功能易于上手，但对于复杂的实验任务，用户可能需要深入了解 `jsPsych` 的内部机制和插件系统。
2. **性能问题**：对于非常复杂的实验或大量的数据收集，`jsPsych` 可能会出现性能问题。尤其是在移动设备上，渲染和响应速度可能较慢。
3. **浏览器兼容性**：虽然 `jsPsych` 兼容大多数现代浏览器，但在某些旧版浏览器或不常见的浏览器中，可能会遇到兼容性问题。

### 5.使用建议

1. **开始之前阅读文档**：在开始使用 `jsPsych` 之前，建议详细阅读其 [官方文档](https://www.jspsych.org/) 和 [示例代码](https://www.jspsych.org/examples/)，以了解基本概念和常用功能。
2. **逐步构建实验**：从简单的实验任务开始，逐步添加复杂的功能。这样可以逐步掌握 `jsPsych` 的使用技巧，并减少调试的难度。
3. **利用社区资源**：加入 `jsPsych` 的社区论坛或邮件列表，利用社区的资源来解决遇到的问题。社区中的其他研究人员和开发者常常能够提供有价值的帮助和建议。
4. **测试跨浏览器兼容性**：在实验设计完成后，确保在不同的浏览器和设备上进行测试，以确保实验的兼容性和稳定性。

### 好了，接下来我们试一下创建jspsych实验程序吧！

首先，确保您的电脑安装了代码编辑器：Visual studio Code，然后我们开始吧！

## 第一步：设置HTML页面结构

首先，我们需要创建一个HTML文件，这是我们网页的基础结构。这个文件将包含所有的实验内容。

### 创建基本的HTML文件

1. 打开一个文本编辑器（如Notepad、Sublime Text或Visual Studio Code）。
2. 创建一个新文件，保存为 `index.html`。
3. 在文件中添加以下代码，这是标准的HTML页面结构：

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>心理学实验：叙事疗法的魔力</title>
    </head>
    <body></body>
    </html>
    ```
## 第二步：引入jsPsych库

jsPsych是一个用于创建心理学实验的JavaScript库。我们需要将jsPsych及其插件添加到我们的HTML文件中。

### 1. 下载jsPsych库

从[jsPsych的GitHub页面](https://github.com/jspsych/jsPsych)下载最新版本，并解压到你的项目文件夹中。确保你的项目结构如下：
### 2. 引入jsPsych及其插件

在你的HTML文件的 `<head>` 部分中，添加以下代码以引入jsPsych库及其插件：

```
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>心理学实验：叙事疗法的魔力</title>
    <!-- 引入jsPsych库 -->
    <script src="./jspsych/jspsych.js"></script>
    <!-- 引入jsPsych插件 -->
    <script src="./jspsych/plugins/jspsych-html-keyboard-response.js"></script>
    <script src="./jspsych/plugins/jspsych-survey-text.js"></script>
    <script src="./jspsych/plugins/jspsych-survey-multi-choice.js"></script>
    <script src="./jspsych/plugins/jspsych-preload.js"></script>
    <script src="./jspsych/plugins/jspsych-image-keyboard-response.js"></script>
    <!-- 引入jsPsych样式表 -->
    <link href="./jspsych/css/jspsych.css" rel="stylesheet" type="text/css">
    <!-- 引入自定义样式表 -->
    <link rel="stylesheet" href="./style.css">
</head>
```
## 第三步：初始化jsPsych ##
接下来，我们需要在 <script> 标签中初始化jsPsych。这一步是在网页加载完毕后，准备好jsPsych运行所需的环境。

1. 初始化jsPsych
在HTML文件的 <body> 部分中，添加一个 <script> 标签，并在其中初始化jsPsych：
```
    <body></body>
    <script>
    const jsPsych = initJsPsych(); // 初始化jsPsych
    </script>
```
### 完整代码:
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>心理学实验：叙事疗法的魔力</title><!-- 初始化html -->
    <script src="./jspsych/jspsych.js"></script>
    <script src="./jspsych/plugin-html-keyboard-response.js"></script>
    <script src="./jspsych/plugin-survey-text.js"></script>
    <script src="./jspsych/plugin-survey-multi-choice.js"></script>
    <script src="./jspsych/plugin-preload.js"></script>
    <script src="./jspsych/plugin-image-keyboard-response.js"></script><!-- 初始化jspsych -->
    <link href="./jspsych/jspsych.css" rel="stylesheet" type="text/css">
    <link rel="stylesheet" href="./style.css"> <!-- 初始化CSS文件 -->
</head>
<body></body>
<script>
     const jsPsych = initJsPsych();/* 初始化jsPsych */
</script>
```
代码解析：
- `<!DOCTYPE html>`声明文档类型为HTML5。
- `<html lang="en">`定义HTML文档的语言为英语。
- `<head>`包含文档的元数据（如文档标题和引用的CSS、JavaScript文件）。
- `<meta charset="UTF-8">`设置字符编码为UTF-8。
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">`确保页面在不同设备上正常显示。
- `<title>`定义网页标题。
- `<script>`引入jsPsych库和相关插件。
- `<link>`引入jsPsych的CSS文件和自定义样式文件。
- `<body>`文档的主体内容。


## 第四步：创建欢迎界面 ##
现在我们可以开始创建实验的第一个部分——欢迎界面。这个界面将向参与者展示一个欢迎信息，并等待他们按下任意键继续，包括：
- 1.创建一个名为 welcome 的变量，用于存储欢迎界面的配置信息。

- 2.设置类型为 jsPsychHtmlKeyboardResponse，表示这是一个HTML键盘响应类型的任务。

- 3.在 stimulus 属性中，定义要显示的HTML内容。这段HTML内容将显示一段欢迎辞，并指导参与者按任意键开始实验。

在 <script> 标签中，添加以下代码来创建一个欢迎界面：

```
<script>
    const jsPsych = initJsPsych(); // 初始化jsPsych

    // 欢迎界面
    var welcome = {
        type: jsPsychHtmlKeyboardResponse,
        stimulus: `<p id="end"><span style="color:red;font-size:50px;align-items: center;"><br><br>欢迎参加本次心理学实验</span><br><br><br><br><br><br>
                   <span style="font-weight:bold">本实验的目的是想让您了解并体验一种心理咨询的方法：叙事疗法<br><br>请保证周围环境安静并用心思考作答,相信您会藉此体会到叙事疗法的乐趣。</span><br><br><br><br><br><br><br><br><br>您的数据将会被上传到安全保密的实验数据库，仅作科研用途<br>
                   感谢您参与我们的实验，如果您准备好了,请按<span style="color: red">任意键</span>开始实验吧!</p>`
    };

    // 运行实验
    jsPsych.run([welcome]);
</script>
```
## 第五步：创建前测问卷 ##
前测问卷将收集参与者在实验开始前的一些基本信息和情绪状态。这部分问卷将使用jsPsych的 jspsych-survey-text 和 jspsych-survey-multi-choice 插件。
### 1. 创建前测问卷的文本部分
首先，我们创建一个包含开放性问题的前测问卷部分，包括：
- 1. 创建一个名为 `pretest1` 的变量，用于存储前测问卷的配置信息。
- 2. 设置类型为 `jsPsychSurveyText`，表示这是一个文本输入类型的问卷。
- 3. 在 `preamble` 属性中，定义问卷的前言。
- 4. 在 `questions` 属性中，定义具体的问题列表，每个问题包括 `prompt`、`rows` 和 `columns` 属性，分别表示问题的提示文本、行数和列数。
- 5. 设置 `button_label` 属性为 '继续'，表示按钮的标签。
 代码如下：
```
<script>
    const jsPsych = initJsPsych(); // 初始化jsPsych

    // 欢迎界面
    var welcome = {
        type: jsPsychHtmlKeyboardResponse,
        stimulus: `<p id="end"><span style="color:red;font-size:50px;align-items: center;"><br><br>欢迎参加本次心理学实验</span><br><br><br><br><br><br>
                   <span style="font-weight:bold">本实验的目的是想让您了解并体验一种心理咨询的方法：叙事疗法<br><br>请保证周围环境安静并用心思考作答,相信您会藉此体会到叙事疗法的乐趣。</span><br><br><br><br><br><br><br><br><br>您的数据将会被上传到安全保密的实验数据库，仅作科研用途<br>
                   感谢您参与我们的实验，如果您准备好了,请按<span style="color: red">任意键</span>开始实验吧!</p>`
    };

    // 前测问卷文本部分
    var pretest1 = {
        type: jsPsychSurveyText,
        preamble: '首先,请填写以下问卷',
        questions: [
            {prompt: '1.最近,最困扰您的问题是：', rows: 2, columns: 100},
            {prompt: '2.可以详细聊聊吗?', rows: 6, columns: 100},
            {prompt: '3.每次出现这个问题,您内心都会产生怎样的感受呢?', rows: 6, columns: 100},
        ],
        button_label: '继续',
    };

    // 运行实验
    jsPsych.run([welcome, pretest1]);
</script>
```
### 2. 创建前测问卷的选择题部分
接下来，我们创建一个包含选择题的前测问卷部分，包括：
- 1. 创建一个名为 `pretest2` 的变量，用于存储前测指标的配置信息。
- 2. 设置类型为 `jsPsychSurveyMultiChoice`，表示这是一个多选类型的问卷。
- 3. 在 `preamble` 属性中，定义问卷的前言。
- 4. 在 `questions` 属性中，定义具体的问题列表，每个问题包括 `prompt`、`name`、`options`、`required` 和 `horizontal` 属性，分别表示问题的提示文本、名称、选项、是否必填和是否水平排列。
- 5. 设置 `button_label` 属性为 '继续'，表示按钮的标签。
  代码如下：
```
<script>
    // 前测问卷选择题部分
    var pretest2 = {
        type: jsPsychSurveyMultiChoice,
        preamble: '请选择：',
        questions: [
            {
                prompt: "1.现在,您的心情如何？(1~10程度逐渐升高,1是极其低落,10是非常愉悦)",
                name: 'mood1', 
                options: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'],
                required: true
            },
            {
                prompt: "2.最近一周,您内心的压力感受如何？(1~10程度逐渐升高,1是没有压力,10是非常大的压力)",
                name: 'stress1', 
                options: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'],
                required: true
            }
        ],
        button_label: '继续'
    };
</script>
```

## 第六步：创建叙事疗法引导页面 ##
接下来，我们创建一个页面，用于引导参与者进入叙事疗法的情境,和欢迎界面一样，这部分将使用jspsych-html-keyboard-response插件。
```
     var illustrate = {
      type: jsPsychHtmlKeyboardResponse,
      stimulus: `<p id = illustrate><br><br><br><br><br><br><br><br><span style ="font-weight:bold">我们听过的故事影响着我们的生活，而我们所讲的故事定义了我们自己。
                  <br><br>您的问题一定给您带来了诸多烦恼吧，现在，请您深呼吸并尽量放松。</span><br><br><br><br><br>
                  接下来我们将给您呈现一系列图片来转换您的注意力。<br>
                  请您给每个图片编<span style ="color: red">两个截然不同</span>的故事。<br><br>
                  每个故事编完之后再总结一下这张图片给您的感受吧!<br><br><br>
                  不需说出来,请用心体会叙事带来的力量......<br>
                  (按<span style ="color: red">任意键</span>开始)</p>
                  `
     };
```

## 第七步：创建叙事疗法任务 ##
在这一步中，我们将创建一个页面，呈现图片让被试自己编故事，编完按空格进入下一页面。这部分将使用jspsych-survey-text插件，包括：
- 1. 创建一个名为 `preload` 的变量，用于存储实验前加载资源的配置信息。
- 2. 设置类型为 `jsPsychPreload`，表示这是一个资源预加载任务，确保在实验开始前，所有必需的资源都已经加载完成。
- 3. 设置 `auto_preload` 属性为 `true`，表示自动加载所有需要的资源。
- 4. 创建名为 `image1` 的变量，用于存储显示第一张图片的配置信息。
- 5. 设置类型为 `jsPsychImageKeyboardResponse`，表示这是一个图像键盘响应类型的任务。
- 6. 在 `stimulus` 属性中，指定图片的路径。设置 `render_on_canvas` 为 `false`，表示不在画布上渲染图像，直接显示图片。
- 7. 设置 `choices` 属性为 `[' ']`，表示参与者按空格键继续。
- 8. 设置 `stimulus_width` 为 `800`，定义图像的宽度。
- 9. 在 `prompt` 属性中，定义显示的提示文本，指导参与者按空格键继续。
- 10. 创建名为 `image2` 的变量，用于存储显示第二张图片的配置信息。设置与 `image1` 类似的属性，确保显示第二张图片。
代码如下：
```
<script>
     var preload = {
      type: jsPsychPreload,
      auto_preload: true
     };
     
     var image1 = {
     type: jsPsychImageKeyboardResponse,
     stimulus: './Stimuli/images/image3.jpg',
     render_on_canvas: false,
     choices: [' '],
     stimulus_width:800,
     prompt:'<p>按空格键继续</p>'
     };

     var image2 = {
     type: jsPsychImageKeyboardResponse,
     stimulus: './Stimuli/images/image2.jpg',
     render_on_canvas: false,
     choices: [' '],
     stimulus_width:800,
     prompt:'<p>按空格键继续</p>'
     };
</script>
```


## 第八步：创建后测问卷和结束界面 ##
最后，我们创建一个后测问卷和结束界面，感谢参与者并告知他们实验结束。这部分和前测问卷与说明界面用到的插件一样，实现方法参考前面这两个部分。
代码如下：
```
   /* 后测问卷 */
     var Post_test1 = {
      type: jsPsychSurveyText,
      preamble: '<p id = Post_test_premble>叙事是一种力量,找到新的叙事,您就找到了新的力量源泉,也就有了解决问题的资源。下面,请仔细思考下面的问题:</p>',
      questions: [
       {prompt: '1.如果要给您的问题给一个命名,根据它带来的感受,您会把它命名成:(比如:小房间、瘪掉的气球、大黑狗等等)',rows:1,columns:120},
       {prompt: '2.问什么给予它这个名字,您能详细地定义一下它么?', rows:2,columns:120},
       {prompt: '3.结合前面叙事的经验,请问您可以从另一个角度来描述自己的问题吗?', rows:6,columns:120},
       {prompt: '4.如此,结合您以前成功经验,您觉得这个问题可以从哪些角度尝试着解决呢?', rows:6,columns:120},
        ],          
        button_label : '继续',
     };

     /* 后测指标 */
     var Post_test2 = {
      type: jsPsychSurveyMultiChoice,
      preamble: '<p id = Post_test2_preamble><span style = "color: red">恭喜您!</span><br><br>通过对叙事疗法的了解和一些的简单训练,您对您的问题又有了新的见解。在面对问题时,请带着这份知识和见解冷静地思考对策吧！<br><br>最后,请再做一次下面的选择:</p>',
      questions: [
      {
      prompt: "1.现在,您的心情如何？(1~10程度逐渐升高,1是极其低落,10是非常愉悦)",                                                
      name: 'mood2', 
      options: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'], 
      required: true,
      horizontal: true
      },
      {
      prompt: "2.假设这个问题再次出现,您有多大把握可以成功解决它或者将它的影响降到最低？(1~10程度逐渐升高,1是完全无望,10是很有信心)", 
      name: 'confidence2', 
      options: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'], 
      required: true,
      horizontal: true
      }, 
       ],
       button_label : '继续',
     };

     /* 结束界面 */
     var end = {
      type: jsPsychHtmlKeyboardResponse,
      stimulus: `<p id = end><span style = "color:red;font-size:50px;align-items: center;"><br><br>感谢您的参与!</span><br><br><br><br><br><br><br>
                 <span style ="font-weight:bold">叙事是每个人都会的技能,发现叙事的力量并利用它,能够将我们自己抽身于问题之外,我们的人生就会有无限种可能。</span>
                 <br><br><br><br><br><br><br><br><br><br>叙事疗法的经典书籍:《叙事治疗的力量：故事、知识、权力》——作者: [澳] 迈克尔·怀特 / [新西兰] 戴维·爱普斯顿<br>
                 如果有任何问题,欢迎与主试交流:kailiangge@yeah.net</p>
                  `,
      choices: "NO_KEYS",
     };
```

## 完整的.html文件代码 ##
最后，再加上按时间线运行的语句：Run使得实验可以跑起来，下面是将所有部分组合在一起的完整HTML代码：
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>心理学实验：叙事疗法的魔力</title><!-- 初始化html -->
    <script src="./jspsych/jspsych.js"></script>
    <script src="./jspsych/plugin-html-keyboard-response.js"></script>
    <script src="./jspsych/plugin-survey-text.js"></script>
    <script src="./jspsych/plugin-survey-multi-choice.js"></script>
    <script src="./jspsych/plugin-preload.js"></script>
    <script src="./jspsych/plugin-image-keyboard-response.js"></script><!-- 初始化jspsych -->
    <link href="./jspsych/jspsych.css" rel="stylesheet" type="text/css">
    <link rel="stylesheet" href="./style.css"> <!-- 初始化CSS文件 -->
</head>
<body></body>
<script>
     const jsPsych = initJsPsych();/* 初始化jsPsych */
     
     /* 欢迎界面 */
     var welcome = {
      type: jsPsychHtmlKeyboardResponse,
      stimulus: `<p id = end><span style = "color:red;font-size:50px;align-items: center;"><br><br>欢迎参加本次心理学实验</span><br><br><br><br><br><br>
                 <span style ="font-weight:bold">本实验的目的是想让您了解并体验一种心理咨询的方法：叙事疗法<br><br>请保证周围环境安静并用心思考作答,相信您会藉此体会到叙事疗法的乐趣。</span><br><br><br><br><br><br><br><br><br>您的数据将会被上传到安全保密的实验数据库，仅作科研用途<br>
                 感谢您参与我们的实验，如果您准备好了,请按<span style ="color: red">任意键</span>开始实验吧!</p>
                  `
     };

     /* 前测问卷 */
     var pretest1 = {
      type: jsPsychSurveyText,
      preamble: '首先,请填写以下问卷',
      questions: [
       {prompt: '1.最近,最困扰您的问题是：',rows:2,columns:100},
       {prompt: '2.可以详细聊聊吗?', rows:6,columns:100},
       {prompt: '3.每次出现这个问题,您内心都会产生怎样的感受呢?', rows:6,columns:100},
        ],          
        button_label : '继续',
     };

     /* 前测指标 */
     var pretest2 = {
      type: jsPsychSurveyMultiChoice,
      preamble: '请选择：',
      questions: [
      {
      prompt: "1.现在,您的心情如何？(1~10程度逐渐升高,1是极其低落,10是非常愉悦)",                                                
      name: 'mood1', 
      options: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'], 
      required: true,
      horizontal: true
      },
      {
      prompt: "2.假设这个问题再次出现,您有多大把握可以成功解决它或者将它的影响降到最低？(1~10程度逐渐升高,1是完全无望,10是很有信心)", 
      name: 'confidence1', 
      options: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'], 
      required: true,
      horizontal: true
      }, 
       ],
       button_label : '继续',
     };

     /* 实验的说明 */
     var illustrate = {
      type: jsPsychHtmlKeyboardResponse,
      stimulus: `<p id = illustrate><br><br><br><br><br><br><br><br><span style ="font-weight:bold">我们听过的故事影响着我们的生活，而我们所讲的故事定义了我们自己。
                  <br><br>您的问题一定给您带来了诸多烦恼吧，现在，请您深呼吸并尽量放松。</span><br><br><br><br><br>
                  接下来我们将给您呈现一系列图片来转换您的注意力。<br>
                  请您给每个图片编<span style ="color: red">两个截然不同</span>的故事。<br><br>
                  每个故事编完之后再总结一下这张图片给您的感受吧!<br><br><br>
                  不需说出来,请用心体会叙事带来的力量......<br>
                  (按<span style ="color: red">任意键</span>开始)</p>
                  `
     };

     /* 进行实验 */
     var preload = {
      type: jsPsychPreload,
      auto_preload: true
     };
     
     var image1 = {
     type: jsPsychImageKeyboardResponse,
     stimulus: './Stimuli/images/image3.jpg',
     render_on_canvas: false,
     choices: [' '],
     stimulus_width:800,
     prompt:'<p>按空格键继续</p>'
     };

     var image2 = {
     type: jsPsychImageKeyboardResponse,
     stimulus: './Stimuli/images/image2.jpg',
     render_on_canvas: false,
     choices: [' '],
     stimulus_width:800,
     prompt:'<p>按空格键继续</p>'
     };

    /* 后测问卷 */
     var Post_test1 = {
      type: jsPsychSurveyText,
      preamble: '<p id = Post_test_premble>叙事是一种力量,找到新的叙事,您就找到了新的力量源泉,也就有了解决问题的资源。下面,请仔细思考下面的问题:</p>',
      questions: [
       {prompt: '1.如果要给您的问题给一个命名,根据它带来的感受,您会把它命名成:(比如:小房间、瘪掉的气球、大黑狗等等)',rows:1,columns:120},
       {prompt: '2.问什么给予它这个名字,您能详细地定义一下它么?', rows:2,columns:120},
       {prompt: '3.结合前面叙事的经验,请问您可以从另一个角度来描述自己的问题吗?', rows:6,columns:120},
       {prompt: '4.如此,结合您以前成功经验,您觉得这个问题可以从哪些角度尝试着解决呢?', rows:6,columns:120},
        ],          
        button_label : '继续',
     };

     /* 后测指标 */
     var Post_test2 = {
      type: jsPsychSurveyMultiChoice,
      preamble: '<p id = Post_test2_preamble><span style = "color: red">恭喜您!</span><br><br>通过对叙事疗法的了解和一些的简单训练,您对您的问题又有了新的见解。在面对问题时,请带着这份知识和见解冷静地思考对策吧！<br><br>最后,请再做一次下面的选择:</p>',
      questions: [
      {
      prompt: "1.现在,您的心情如何？(1~10程度逐渐升高,1是极其低落,10是非常愉悦)",                                                
      name: 'mood2', 
      options: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'], 
      required: true,
      horizontal: true
      },
      {
      prompt: "2.假设这个问题再次出现,您有多大把握可以成功解决它或者将它的影响降到最低？(1~10程度逐渐升高,1是完全无望,10是很有信心)", 
      name: 'confidence2', 
      options: ['1', '2', '3', '4', '5', '6', '7', '8', '9', '10'], 
      required: true,
      horizontal: true
      }, 
       ],
       button_label : '继续',
     };

     /* 结束界面 */
     var end = {
      type: jsPsychHtmlKeyboardResponse,
      stimulus: `<p id = end><span style = "color:red;font-size:50px;align-items: center;"><br><br>感谢您的参与!</span><br><br><br><br><br><br><br>
                 <span style ="font-weight:bold">叙事是每个人都会的技能,发现叙事的力量并利用它,能够将我们自己抽身于问题之外,我们的人生就会有无限种可能。</span>
                 <br><br><br><br><br><br><br><br><br><br>叙事疗法的经典书籍:《叙事治疗的力量：故事、知识、权力》——作者: [澳] 迈克尔·怀特 / [新西兰] 戴维·爱普斯顿<br>
                 如果有任何问题,欢迎与主试交流:kailiangge@yeah.net</p>
                  `,
      choices: "NO_KEYS",
     };

     /* 按时间线运行 */
     jsPsych.run([welcome,pretest1,pretest2,illustrate, preload, image1,image2,Post_test1,Post_test2,end]);

</script>
</html>
```
## 用CSS添加样式 ##

### 1.什么是 CSS？

**CSS**（层叠样式表，Cascading Style Sheets）是一种用于描述 HTML 或 XML 文档（包括 SVG 和 XHTML）的样式的语言。CSS 控制网页的视觉呈现和布局，使得开发者可以在不改变文档结构的情况下调整其样式和布局。

### 2.CSS 的基本概念

1. **选择器**：选择器用于选择 HTML 元素，以便对这些元素应用样式。常见的选择器包括元素选择器（如 `p`）、类选择器（如 `.class-name`）、ID 选择器（如 `#id-name`）等。

2. **属性和属性值**：CSS 样式由属性和属性值组成。属性定义了要应用的样式，属性值则指定了样式的具体内容。例如，`color: red;` 这段 CSS 代码设置了文本颜色为红色。

3. **规则集**：CSS 规则集由选择器和声明块组成。声明块包含一个或多个属性和属性值对。规则集的语法如下：
   ```css
   selector {
       property: value;
       property: value;
   }
   ```

4. **层叠和继承**：CSS 的 "层叠" 和 "继承" 特性使得样式可以层叠和继承。例如，如果某个元素的特定样式没有被定义，它将会继承其父元素的样式。

### 3.CSS 的基本语法

CSS 规则的基本语法如下：

```css
selector {
    property: value;
}
```

### 示例

```css
/* 选择所有的 <h1> 元素 */
h1 {
    color: blue; /* 设置文本颜色为蓝色 */
    font-size: 24px; /* 设置字体大小为 24 像素 */
}

/* 选择所有具有 class="highlight" 的元素 */
.highlight {
    background-color: yellow; /* 设置背景颜色为黄色 */
    font-weight: bold; /* 设置字体加粗 */
}

/* 选择 ID 为 "header" 的元素 */
#header {
    text-align: center; /* 设置文本居中对齐 */
}
```

### 4.CSS 的优点

1. **分离内容和样式**：CSS 允许将文档的内容（HTML）与样式（CSS）分开，使得文档的结构更加清晰和易于维护。

2. **提高重用性**：通过定义样式类，可以在多个页面中重用相同的样式，提高了代码的重用性和一致性。

3. **响应式设计**：CSS 支持响应式设计，通过媒体查询（media queries）可以创建适应不同设备和屏幕尺寸的布局。

4. **提升用户体验**：CSS 提供了丰富的视觉效果，如动画、过渡效果等，可以显著提升用户体验。

## CSS 的缺点

1. **浏览器兼容性**：不同浏览器可能对 CSS 的支持程度有所不同，这可能导致跨浏览器显示不一致的问题。

2. **学习曲线**：虽然 CSS 基础易学，但高级特性和复杂布局可能需要较长的学习时间。

3. **性能问题**：大量的 CSS 规则和复杂的样式可能会影响网页的渲染性能。

### 5.使用建议

1. **使用外部样式表**：将 CSS 样式放在外部样式表中，而不是嵌入到 HTML 文件中，这样可以提高代码的可维护性和重用性。

2. **利用现代 CSS 特性**：使用 Flexbox 和 Grid 布局来创建响应式和灵活的布局，这些特性可以简化复杂的布局问题。

3. **编写可维护的代码**：遵循命名规范，保持 CSS 代码整洁和有序，便于团队协作和后期维护。

4. **测试跨浏览器兼容性**：确保在不同的浏览器和设备上测试样式，确保网页在各种环境下的正常显示。

### 6.编写CSS样式表`style.css`文件

注意：`#`用来选择某ID，`.`用来选择某Class.

具体的控制代码可以在下面的网站中翻找：[www.w3school.com.cn](www.w3school.com.cn)

这里只是做一个示例

在style.css中打出如下代码来选择并定义实验的样式：

```
/* 定义页面和刺激的flexbox属性 */
body {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: white;
    height: 100vh;
    width: 100vw;
    margin: 0;
}
#jspsych-content {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: white;
    height: 100vh;
    width: 100vw;
    margin: 0;
}

/* 欢迎界面 */
/* #welcome {
    color : black;
    justify-content: center;
    align-items: center;
    background-color: white;
    font-size:  20px;
    height: 600px;
} */

/* 问卷1界面 */
#jspsych-survey-text-preamble {
    color : black;
    background-color: white;
    font-size:  30px;
    font-weight: bold;
    height: 50px;
}
.jspsych-survey-text{
    text-align: left;
    margin: 5px;
}
#input-0{
    font-family: Arial, Helvetica, sans-serif;
    font-size:  15px;
}
#input-1{
    font-family: Arial, Helvetica, sans-serif;
    font-size:  15px;
}
#input-2{
    font-family: Arial, Helvetica, sans-serif;
    font-size:  15px;
}
 
/* 选择1界面 */
#jspsych-survey-multi-choice-preamble{
    color : black;
    background-color: white;
    font-size:  30px;
    font-weight: bold;
    height: 50px;
}
p.jspsych-survey-multi-choice-text.survey-multi-choice{
    text-align: left;
    white-space: wrap;
}
.jspsych-survey-multi-choice-option{
    display: flex;
    flex-wrap: wrap;
}

/* 说明1界面 */
#illustrate{
    color : black;
    justify-content: center;
    align-items: center;
    background-color: white;
    font-size:  20px;
    height: 600px;
}

/* 问卷2界面 */
#Post_test_premble {
    color : black;
    background-color: white;
    font-size:  20px;
    font-weight: bold;
    height: 50px;
}
#input-3{
    font-family: Arial, Helvetica, sans-serif;
    font-size:  15px;
}

/* 选择2界面 */
#Post_test2_preamble{
    color : black;
    background-color: white;
    font-size:  20px;
    font-weight: bold;
    height: 50px;
    position: relative;
    bottom: 100px;
}
```






