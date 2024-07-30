# 心理学实验程序教程

## 第一步：设置HTML页面结构

首先，我们需要创建一个HTML文件，这是我们网页的基础结构。这个文件将包含所有的实验内容。

### 1. 创建基本的HTML文件

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
```
## 九、完整代码 ##
下面是将所有部分组合在一起的完整HTML代码：

html
复制代码
<!DOCTYPE html>
<html lang="en">
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
<body>
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

    // 叙事疗法引导页面
    var narrative_intro = {
        type: jsPsychHtmlKeyboardResponse,
        stimulus: `<p id="end"><span style="color:red;font-size:50px;align-items: center;"><br><br>叙事疗法</span><br><br><br><br><br><br>
                   <span style="font-weight:bold">请您回想一个令您感到困扰的经历，并尝试通过叙述这个经历来理解和面对它。</span><br><br><br><br><br><br><br><br><br>
                   如果您准备好了,请按<span style="color: red">任意键</span>继续。</p>`
    };

    // 叙事疗法任务
    var narrative_task = {
        type: jsPsychSurveyText,
        preamble: '请描述您的经历',
        questions: [
            {prompt: '请详细描述这段经历。', rows: 10, columns: 100},
            {prompt: '在这个经历中，您感受到了什么？', rows: 6, columns: 100},
            {prompt: '您认为这段经历对您的生活产生了什么影响？', rows: 6, columns: 100}
        ],
        button_label: '提交'
    };

    // 结束页面
    var end = {
        type: jsPsychHtmlKeyboardResponse,
        stimulus: `<p id="end"><span style="color:red;font-size:50px;align-items: center;"><br><br>实验结束</span><br><br><br><br><br><br>
                   <span style="font-weight:bold">感谢您的参与
