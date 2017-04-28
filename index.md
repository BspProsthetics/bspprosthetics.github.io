## BioSignal Prosthetics
### _Powering the prosthetic devices of tomorrow_

### Authors
Anjulie Agrusa, Nick Harrington, Austin Lefebvre, Carlo Mazzaferro, Nicolle Woo

### Mentors
Dr. Todd Coleman, Dr. Shankar Subramaniam

### Acknowledgements
Qusp, Cognionics

Check out this video for a live demo:

<iframe src="https://player.vimeo.com/video/208059205" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/208059205">BioSignal Prosthetics Demo Video</a> from <a href="https://vimeo.com/lakehousevideo">Josh Lake</a> on <a href="https://vimeo.com">Vimeo</a>.</p>


## Outline of The Project Proposal
<a id = "toc"></a>
1. <a href = "Quick_Look"> Quick Look</a>
2. <a href = "#Introduction"> Introduction</a>
3. <a href = "#bg_info">Relevant Background Information</a>
4. <a href = "#prop">Proposed Design Solution: EEG + EMG Controlled Prosthetics </a>
5. <a href = "#imp">Implementation Details</a>
6. <a href = "#disc">Discussion and Conclusion</a>
7. <a href = "#bib">Bibliography</a>

<a id = "Quick_Look"></a>
## Quick Look 
![](https://raw.githubusercontent.com/BspProsthetics/bspprosthetics.github.io/master/BSP_pic.png)

- Current upper limb prosthetics are often difficult to use, unintuitive, or require surgery
- Our solution provides both intuitive control and multiple degrees of freedom
- We do this by using EEG and EMG methods of control
- The EEG is performed with an EEG headset and connects via Bluetooth to the prosthetic
- The user’s motor intent is predicted by a machine learning algorithm and controls the opening
and closing motions
- The EMG is controlled by electrodes on the bicep and connected via wires to control the
prosthetic wrist rotation

<a id = "Introduction"></a>
## Introduction
  Current upper limb prosthetics are often either difficult to control or incredibly expensive and invasive. The simpler prosthetics require the user to either flex or lift their arm to control their prosthetic device, which is limiting and not intuitive, while the more expensive devices require extensive surgery and physical remapping of the patient’s nerves. Our design implementes a solution based on motor intent control via brain waves in addition to traditional myoelectric (muscle) control. This is all done non-invasively and is specifically designed to be compatible with 3-D printed prosthetics and will thereby work for even the cheapest of prosthetic devices. 
    The brainwave control is accomplished by taking data gathered from an EEG headset and using machine learning algorithms to detect if the user is thinking about opening or closing their hand. This signal is then sent via Bluetooth to the prosthetic device, or in our case, a robotic hand for demonstration purposes. 
    The EMG control uses electrodes placed on the upper arm to detect if the user is flexing, which then sends a signal to the prosthetic device to rotate the wrist, or in the case of an actual prosthetic device, change the hand position or move the fingers. This overall system will allow the user to feel more in control as well as demonstrate what the future of prosthetics could be like. Future improvements to the device will consist of haptic feedback, increased accuracy, and the elimination of EMG controlled rotation in favor of purely EEG controlled rotation.

<a id = "bg_info"></a>
## Relevant Background Information

  The most simple prosthetic is just a static hook or other tool attached to the person’s arm, without any dynamic movement or control. Body powered prosthetics use another part of the person’s body, often their shoulder, to open and close a hand-like apparatus at the end of the prosthetic device. These prosthetics are more functional than just basic hook or tool, yet they still are simple enough to only require low maintenance and a short adjustment period. The myoelectric, on the other hand, has electrodes attached to a muscle on the patient so that when the patient flexes that muscle, it sends a signal to open or close the prosthetic hand. The benefits of this are that it is more seamless, there’s no need to move a shoulder to close a hand. However, such advanced prosthetics are often very costly, have a steep learning curve, and don’t actually provide that much more functionality than the more simple body powered option [1]. The final type of prosthetics (almost entirely in the research phase) are brain controlled. Currently, these are mostly done invasively as external electrodes have difficulty in gathering an accurate and dependable signal [2]. Electrodes are implanted into the patient’s motor cortex to receive signals of motor intent from the patient, and that data would then be processed and used to control the prosthetic. Clearly, if fully functional, this would be the far better choice as it would allow for an almost seamless use of one’s artificial limb, however the need for electrodes to be implanted surgically is a significant drawback. Additionally, advanced processing of the neural signals is needed for such a system to be accurate [3]. These types of prosthetics are subject to considerable amounts of research, yet no clinical versions are currently available. Overall, much improvement is still needed in this field. Even in the more advanced myoelectric version, the control scheme is still difficult, and even in the best of circumstances, few if any prosthetics can provide the user with force or tactile feedback, making even the simple task of grasping things difficult [4].

<a id = "prop"></a>
## Proposed Design Solution: EEG + EMG Controlled Prosthetics 
![](https://raw.githubusercontent.com/BspProsthetics/bspprosthetics.github.io/master/BSP_Susy2.png)

The design selected allows user's brain signals from the scalp to be collected via an EEG headset. The signal is then sent to the cloud and is processed with software that contains a pipeline that will identify motor intent and translate it into a motor command to the prosthetic. This allows the amputee to feel as though the prosthetic is moving naturally. Additionally, the EMG component will be used to determine fine motor control, such as finger movements. An EMG cuff will be placed around the subject’s forearm, which will pick up muscle contraction biosignals. The implementation costs will come from a quality EEG headset ($4000-$40,000), and a simple myoelectric prosthetic ($3000).

<a id = "imp"></a>
## Implementation Details

The pipeline responsible for the filtering, analyzing, and producing an output is the following:

![](https://raw.githubusercontent.com/BspProsthetics/bspprosthetics.github.io/master/pipeline.png)

Thanks to the folks at [Neuropype](http://neuropype.io/), we were able to use their software for the creation of a real-time suite for EEG data analysis. By hacking into it and cleverly adding processing elements (such as the Gradient Boosting module), we were able to implement out own predictive algorithms. 

<a id = "disc"></a>
## Discussion & Conclusion
The final design met the requirements by enabling a full-blown pipeline that implements methods for data acquisition, processing, analysis and output evaluation. In particular, the final product enables a user to control a prosthetic device based on inputs coming from his or her body with reasonable accuracy. Despite the design challenges that a real-time pipeline targeting oftentimes extremely noisy data can carry, the design proposed meets the goal initially proposed. By combining the intuitiveness of mind-controlled open-close action and the precision of EMG signal transduction, we were able to develop a working prototype of that could enhance a debilitated person’s mobility. Nonetheless, challenges exist. In particular, wearing the device for extended periods of time can be painful to the user, and obtaining signal with low noise values requires constant adjustments to the headset. More research and development should be directed towards these areas, which will enable the product to be more widely validated, tested and adopted.



<a id = "rec"></a>
## Recommendations
Many important additional features and modifications should be considered for further work on the EEG controlled prosthetic arm system. These improvements fall into two categories.

The first, is the software component. The latency of our device is quite poor, with a delay between intent and action of approximately 10 seconds. This delay is likely due to the many various connections between devices used, that is, connections between EEG to Neuropype, to Python, to Arduino, to Bluetooth, to the prosthetic arm. By developing a way to decrease the amount of necessary intermediate connections between EEG, Neuropype, and the prosthetic arm, there will be an improved latency and quicker reaction of the arm. Additionally, further work can be implemented into the machine learning algorithms in order to improve accuracy. The algorithms could also be used to interpret and classify additional EEG patterns in order to differentiate between the intent to move specific fingers, and with specific amounts of force. For future development, the actual purchase (rather than the occasional rental) of an EEG device would be of great use to more frequently test and train the machine learning algorithms. A possible additional modification of the device may include haptic feedback (either through vibration or actual nerve stimulation).

The second area for improvement, is for the hardware. For example, rather than having a hand made of servos, duct tape, and coat hangers, an actual 3D-printed hand could have been created. This hand could have functionality of all 5 fingers and of the wrist, rather than having a single servo controlling only the thumb, and another servo controlling the rotation of the wrist. Furthermore, a more concealed housing for the breadboard, wires, and Arduinos can be developed. This housing should make sure to properly avoid disconnecting loose wires, as ours often did. This housing should also make sure to properly shield the wires between electrodes and the Arduino to avoid any electromagnetic interference, and thus noise. All of this could be accomplished by using the Exiii HACKberry, a 3D printed prosthetic arm from a start up in Japan (pictured on this site).

# TUTORIAL ON HOW TO USE MARKDOWN!!!!!!!!!!!!

You can use the [editor on GitHub](https://github.com/BspProsthetics/bspprosthetics.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/BspProsthetics/bspprosthetics.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
