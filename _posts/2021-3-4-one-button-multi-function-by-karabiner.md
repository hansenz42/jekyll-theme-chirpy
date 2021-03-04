---
layout: post
title: 我用Karabiner：一个按钮，短按长按实现不同功能
date: 2021-3-4
categories:
- 技术笔记
tags:
- karabiner
- MacOS
typora-root-url: ../
---

# Karabiner-Elements
[Karabiner-Elements]([How to map 1 key to simulate holding down multiple keys? · Issue #1637 · pqrs-org/Karabiner-Elements (github.com)](https://github.com/pqrs-org/Karabiner-Elements/issues/1637))是MacOS平台上的一个可自定义键盘按键的软件，开源免费。可以随心所欲地修改键盘，例如：

- 映射按键：可以`capslock`键修改成`ctrl`（我就是这么做的）
- 配置长按和短按的功能：长按`c`映射为`cmd+c`，就可以一键复制
- 配置双击按键：快速双击`v`映射为`cmd+v`，一键粘贴
- 其他更多你能想到的修改

# 为什么我会用Karabiner？因为HHKB
技术宅当然要“调教”自己的生产力工具。不过最主要的原因是最近突然想把几年前买的，一直吃灰的HHKB Pro2键盘用起来。（为什么突然想起来要用呢？大概是想觉得很酷吧！）
HHKB键盘的键位和一般键盘不太一样，据说是为经常使用Unix的工程师设计的。为了在Unix下更好用，把`ctrl`键放在了`capslock`的位置上，这样使用快捷键就更轻松了！

![HHKB键位](/assets/img/post/karabiner-1.png)

<center color=gray>HHKB Pro2键位图，可以看到capslock被control取代了</center>

但是Macbook的键盘布局可不是这样的，为了把使用体验统一起来（处女座上身），我就想到了用Karabiner把Macbook的键位做个映射，调整成与HHKB一样。

# 开始折腾！

## 将capslock与left ctrl互换

设置很简单，在Karabiner的simple-modifications选项卡里把要映射的按钮设置好就行了。

![将capslock与left ctrl按键的位置互换，记得要把设备选为Internal Keyboard，代表配置内置键盘](/assets/img/post/karabiner-2.png)

<center color=gray>将capslock与left ctrl按键的位置互换，记得要把设备选为Internal Keyboard，代表对内置键盘配置</center>

## 设置短按capslock切换输入法

`capslock`映射到`control`的位置以后，切换发现中英文输入法非常不方便，于是我们想实现：

- 短按或单独按`capslock`时切换输入法
- 长按`capslock`时，将`capslock`视为`ctrl`

这样simple-modifications的功能就不够了，我们要编写配置文件，使用complex-modifications来实现。

首先，我们编写以下代码

```json
{
  "title": "My Modifications",
  "rules": [
        {
      "description": "Change left ctrl to ctrl + spacebar.",
      "manipulators": [
        {
          "from": {
            "key_code": "left_control"
          },
          "to": [
            {
              "key_code": "left_control"
            }
          ],
          "to_if_alone": [
            {
              "key_code": "spacebar",
              "modifiers": [
                "left_control"
              ]
            }
          ],
          "type": "basic"
        }
      ]
    }
  ]
}

```

说一下代码：

- `title`是配置组的标题
- `rules`列表是配置组的规则
- `description`是单条配置的描述
- `manipulators`是单条配置中的设置
  - `from`中的`keycode`是**被映射**的按键
  - `to`中的`keycode`是**映射到**的按键，例如想把`a`映射到`b`（按了`a`等于按了`b`），那么就在`from`中写`a`，`to`中写`b`，这里写了`left control`，意思是维持原来的按键不变。
  - `to_if_alone`设置的是，如果只有`from`按下的情况，映射到什么按键。这里设置为`left control + 空格`。意思是如果`capslock`单独按下，那么就触发MacOS切换输入法的快捷键。*（有同学可能会问，为什么不映射到`caps_lock`，我试过，但是在有些应用中切换输入法会不灵敏，经常双击，改成`left control + 空格`以后就不会出现这个问题，具体原因还不知道。）*

然后，将写好的代码保存到` ~/.config/karabiner/assets/complex_modifications/my_modification`。并在karabiner的complex_modifications中启用这个配置。

![](/assets/img/post/karabiner-3.png)

<center font=gray>选择配置界面，点击Enable可以启用</center>

现在，你就可以愉快的把`capslock`当成`ctrl`使用，还可以短按切换输入法。

# 把Tab设置为超级键（Hyper Key）

用了一段时间之后，发现`Tab`的位置也非常好，但是平时又一般使用不到。于是本着不折腾要剁手的态度，想把它做成超级键。

## 什么是“超级键（Hyper Key）”？

超级键就是几个修饰键的组合（`command+ctrl+alt+shift`），按了超级键就相当于同时按下了这四个超级键。

设置超级键有很多好处，其中之一就是我们可以利用它来打造属于自己的快捷键系统，而不会与已有的系统快捷键冲突。

配合[HammerSpoon](https://www.hammerspoon.org/go/)设置快捷键，快速打开各种应用。如果你想使用HammerSpoon，你可以参考[这篇文章](https://sspai.com/post/53992)。也许以后我会聊聊我的独家设置呢。

## 设置超级键

这里我会把`tab`映射到`ctrl+alt+shift`，这样就可以把`cmd`腾出来做`cmd+tab`的组合键。

配置文件：

```json
{
    "title": "My Modification 2",
    "rules": [
        {
            "description": "Change hold tab to shift + control + option.",
            "manipulators": [
                {
                    "from": {
                        "key_code": "tab"
                    },
                    "to": [
                        {
                            "key_code": "left_option",
                            "modifiers": [
                                "left_shift",
                                "left_control"
                            ]
                        }
                    ],
                    "to_if_alone": [
                        {
                            "key_code": "tab"
                        }
                    ],
                    "type": "basic"
                }
            ]
        }
    ]
}
```

按照之前的方式，把配置文件启用就可以了。长按`tab`将会激活超级键，短按则还是制表符。

> 注意，MacOS中`cmd+tab`默认为切换应用。在这个配置下，如果先按了`cmd`再按`tab`，会切换应用，而不会触发超级键。如果想要得到`cmd+tab` = `cmd+ctrl+alt+shift`的效果，要先按`tab`再按`cmd`。

# 后记

这就是我自己的配置，分享给大家，希望有用。这次我们在配置文件里只用到了`to_if_alone`设置，下次有机会我们聊一聊Karabiner中其他几个设置。

