

{:.no_toc}
* toc
{:toc}


# Abstract
Zero-shot online voice conversion (VC) holds significant promise for real-time communications and entertainment. However, current VC models struggle to preserve semantic fidelity under real-time constraints, deliver natural-sounding conversions, and adapt effectively to unseen speaker characteristics.
To address these challenges, we introduce Conan, a chunkwise online zero-shot voice conversion model that preserves the content of the source while matching the voice timbre and styles of reference speech. Conan comprises three core components: 1) a Stream Content Extractor that leverages Emformer for low-latency streaming content encoding; 2) an Adaptive Style Encoder that extracts fine-grained stylistic features from reference speech for enhanced style adaptation; 3) a Causal Shuffle Vocoder that implements a fully causal HiFiGAN using a pixel-shuffle mechanism. Experimental evaluations demonstrate that Conan outperforms baseline models in both subjective and objective metrics。


# Samples
We first show examples of streaming voice conversion on VCTK dataset.

### Example 1
<!-- ── begin copy-paste ───────────────────────────────────────────── -->
<table>
  <thead>
    <tr>
      <th style="text-align: center">Target</th>
      <th style="text-align: center">Reference</th>
      <th style="text-align: center">Conan</th>
      <th style="text-align: center">Conan (fastest)</th>
    </tr>
  </thead>

  <tbody>
    <!-- top row: Target + (Ref / Res / Res) for pair #1 -->
    <tr>
      <!-- Target spans all three reference/result rows -->
      <td rowspan="3" style="text-align: center; vertical-align:middle;">
        <audio controls style="width: 150px;">   <!-- 90 % looks nice on wide tables -->
          <source src="wavs/Change_Spks/eg1/p226_191_mic2.wav" type="audio/wav">
        </audio>
      </td>
      <!-- Reference #1 -->
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg1/p243_005_mic2.wav" type="audio/wav">
        </audio>
      </td>
      <!-- Conan result #1 -->
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg1/full/p243_005_mic2_p226_191_mic2.wav" type="audio/wav">
        </audio>
      </td>
      <!-- Other model result #1 -->
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg1/fastest/p243_005_mic2_p226_191_mic2.wav" type="audio/wav">
        </audio>
      </td>
    </tr>
    <!-- pair #2 -->
    <tr>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg1/p249_011_mic2.wav" type="audio/wav">
        </audio>
      </td>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg1/full/p249_011_mic2_p226_191_mic2.wav" type="audio/wav">
        </audio>
      </td>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg1/fastest/p249_011_mic2_p226_191_mic2.wav" type="audio/wav">
        </audio>
      </td>
    </tr>
    <!-- pair #3 -->
    <tr>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg1/p302_031_mic2.wav" type="audio/wav">
        </audio>
      </td>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg1/full/p302_031_mic2_p226_191_mic2.wav" type="audio/wav">
        </audio>
      </td>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg1/fastest/p302_031_mic2_p226_191_mic2.wav" type="audio/wav">
        </audio>
      </td>
    </tr>
  </tbody>
</table>
<!-- ── end copy-paste ─────────────────────────────────────────────── -->

### Example 2
<!-- ── begin copy-paste ───────────────────────────────────────────── -->
<table>
  <thead>
    <tr>
      <th style="text-align: center">Target</th>
      <th style="text-align: center">Reference</th>
      <th style="text-align: center">Conan</th>
      <th style="text-align: center">Conan (fastest)</th>
    </tr>
  </thead>

  <tbody>
    <!-- top row: Target + (Ref / Res / Res) for pair #1 -->
    <tr>
      <!-- Target spans all three reference/result rows -->
      <td rowspan="3" style="text-align: center; vertical-align:middle;">
        <audio controls style="width: 150px;">   <!-- 90 % looks nice on wide tables -->
          <source src="wavs/Change_Spks/eg2/target.wav" type="audio/wav">
        </audio>
      </td>
      <!-- Reference #1 -->
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg2/ref1.wav" type="audio/wav">
        </audio>
      </td>
      <!-- Conan result #1 -->
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg2/full/gen1.wav" type="audio/wav">
        </audio>
      </td>
      <!-- Other model result #1 -->
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg2/fastest/gen1.wav" type="audio/wav">
        </audio>
      </td>
    </tr>
    <!-- pair #2 -->
    <tr>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg2/ref2.wav" type="audio/wav">
        </audio>
      </td>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg2/full/gen2.wav" type="audio/wav">
        </audio>
      </td>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg2/fastest/gen2.wav" type="audio/wav">
        </audio>
      </td>
    </tr>
    <!-- pair #3 -->
    <tr>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg2/ref3.wav" type="audio/wav">
        </audio>
      </td>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg2/full/gen3.wav" type="audio/wav">
        </audio>
      </td>
      <td style="text-align: center">
        <audio controls style="width: 150px;">
          <source src="wavs/Change_Spks/eg2/fastest/gen3.wav" type="audio/wav">
        </audio>
      </td>
    </tr>
  </tbody>
</table>
<!-- ── end copy-paste ─────────────────────────────────────────────── -->


We then demonstrate the cross-dataset performance of our method. During streaming inference, the entire reference speech is first fed into the model to provide timbre and stylistic information. For chunk-wise online inference, the input is processed once it reaches a predefined chunk size before being passed to the model.

In this experiment, speech from VCTK is used as the target speaker, while speech from LibriTTS serves as the source content. Note that StreamVC is not open-sourced and requires f0 as input; hence, it is excluded from this comparison. All the approaches compared here are **offline voice conversion methods**, which are not designed for streaming inference.

## Target Speaker p231
Target Speech: <audio controls style="width: 30%; margin: 15px 0;"><source src="wavs/Origins/p231_001_002_003.wav" type="audio/wav"> </audio>


<ruby>Text: He hoped there would be stew for dinner, turnips and carrots and bruised potatoes and fat mutton pieces to be ladled out in thick peppered flour-fattened sauce. Stuff it into you, his belly counselled him.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
            <th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
            <th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
            <th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/1.wav" type="audio/wav"></audio></td>

		</tr>
	</tbody>
</table>


<!-- <ruby>Text: You see how doubly, how intimately, opposed the ideas are; yet how difficult to explain without apparent contradiction.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
            <th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
            <th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
            <th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/2.wav" type="audio/wav"></audio></td>

		</tr>
	</tbody>
</table>

<ruby>Text: Or, if not, thou strange and elfish child, whence didst thou come?</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/3.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Ojo was hungry, though; so he divided the piece of bread upon the table and ate his half for breakfast, washing it down with fresh, cool water from the brook.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/4.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table> -->

<ruby>Text: He shrugged his shoulders in ungracious acquiescence, while our visitor in hurried words and with much excitable gesticulation poured forth his story.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<!-- <th style="text-align: center">StreamVC</th> -->
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/5.wav" type="audio/wav"></audio></td>
			<!-- <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/5.wav" type="audio/wav"></audio></td> -->
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/5.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<!-- <ruby>Text: The South she had not thought of seriously; and yet, knowing of its delightful hospitality and mild climate, she was not averse to Charleston or New Orleans..</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/6.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: There Messrs. Johnson and Hammer put into practice many of the ideas now standard in the art, and secured much useful data for the work in New York, of which the story has just been told.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/7.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Here she would stay, comforted and soothed among the lovely plants and rich exotics, rejoicing the heart of Old Turner the gardener, who since Polly's first rapturous entrance, had taken her into his good graces for all time.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/8.wav"  type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<ruby>Text: He examines the horizon all round with his glass, and folds his arms with the air of an injured man.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/9.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby> Text: In order to please her, I spoke to her of the Abbe Conti, and I had occasion to quote two lines of that profound writer.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/10.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table> -->

## Target Speaker p334
Target Speech: <audio controls style="width: 30%; margin: 15px 0;"><source src="wavs/Origins/p334_001_002_003.wav" type="audio/wav"> </audio>

<ruby>Text: He hoped there would be stew for dinner, turnips and carrots and bruised potatoes and fat mutton pieces to be ladled out in thick peppered flour-fattened sauce. Stuff it into you, his belly counselled him.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
            <th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<!-- <th style="text-align: center">StreamVC</th> -->
            <th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
            <th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/1.wav" type="audio/wav"></audio></td>
			<!-- <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/1.wav" type="audio/wav"></audio></td> -->
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/1.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<!-- <ruby>Text: You see how doubly, how intimately, opposed the ideas are; yet how difficult to explain without apparent contradiction.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
            <th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
            <th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
            <th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/2.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Or, if not, thou strange and elfish child, whence didst thou come?</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/3.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Ojo was hungry, though; so he divided the piece of bread upon the table and ate his half for breakfast, washing it down with fresh, cool water from the brook.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/4.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: He shrugged his shoulders in ungracious acquiescence, while our visitor in hurried words and with much excitable gesticulation poured forth his story.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/5.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: The South she had not thought of seriously; and yet, knowing of its delightful hospitality and mild climate, she was not averse to Charleston or New Orleans..</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/6.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: There Messrs. Johnson and Hammer put into practice many of the ideas now standard in the art, and secured much useful data for the work in New York, of which the story has just been told.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/7.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Here she would stay, comforted and soothed among the lovely plants and rich exotics, rejoicing the heart of Old Turner the gardener, who since Polly's first rapturous entrance, had taken her into his good graces for all time.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/8.wav"  type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<ruby>Text: He examines the horizon all round with his glass, and folds his arms with the air of an injured man.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/9.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby> Text: In order to please her, I spoke to her of the Abbe Conti, and I had occasion to quote two lines of that profound writer.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/10.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table> -->

## Target Speaker p362
Target Speech: <audio controls style="width: 30%; margin: 15px 0;"><source src="wavs/Origins/p362_001_002_003.wav" type="audio/wav"> </audio>

<ruby>Text: He hoped there would be stew for dinner, turnips and carrots and bruised potatoes and fat mutton pieces to be ladled out in thick peppered flour-fattened sauce. Stuff it into you, his belly counselled him.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
            <th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<!-- <th style="text-align: center">StreamVC</th> -->
            <th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
            <th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/1.wav" type="audio/wav"></audio></td>
			<!-- <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/1.wav" type="audio/wav"></audio></td> -->
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/1.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<!-- <ruby>Text: You see how doubly, how intimately, opposed the ideas are; yet how difficult to explain without apparent contradiction.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
            <th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
            <th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
            <th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/2.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Or, if not, thou strange and elfish child, whence didst thou come?</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/3.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Ojo was hungry, though; so he divided the piece of bread upon the table and ate his half for breakfast, washing it down with fresh, cool water from the brook.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/4.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: He shrugged his shoulders in ungracious acquiescence, while our visitor in hurried words and with much excitable gesticulation poured forth his story.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/5.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: The South she had not thought of seriously; and yet, knowing of its delightful hospitality and mild climate, she was not averse to Charleston or New Orleans..</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/6.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: There Messrs. Johnson and Hammer put into practice many of the ideas now standard in the art, and secured much useful data for the work in New York, of which the story has just been told.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/7.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Here she would stay, comforted and soothed among the lovely plants and rich exotics, rejoicing the heart of Old Turner the gardener, who since Polly's first rapturous entrance, had taken her into his good graces for all time.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/8.wav"  type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<ruby>Text: He examines the horizon all round with his glass, and folds his arms with the air of an injured man.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/9.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby> Text: In order to please her, I spoke to her of the Abbe Conti, and I had occasion to quote two lines of that profound writer.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/Conan_fastest/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/StreamVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/QuickVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/DiffVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/VQMIVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p362/PPGVC/10.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table> -->

## Target Speaker p360
Target Speech: <audio controls style="width: 30%; margin: 15px 0;"><source src="wavs/Origins/p360_001_002_003.wav" type="audio/wav"> </audio>

<ruby>Text: He hoped there would be stew for dinner, turnips and carrots and bruised potatoes and fat mutton pieces to be ladled out in thick peppered flour-fattened sauce. Stuff it into you, his belly counselled him.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
            <th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
            <th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
            <th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/1.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<!-- <ruby>Text: You see how doubly, how intimately, opposed the ideas are; yet how difficult to explain without apparent contradiction.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
            <th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
            <th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
            <th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/2.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Or, if not, thou strange and elfish child, whence didst thou come?</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: ce/nter">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/3.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Ojo was hungry, though; so he divided the piece of bread upon the table and ate his half for breakfast, washing it down with fresh, cool water from the brook.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/4.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: He shrugged his shoulders in ungracious acquiescence, while our visitor in hurried words and with much excitable gesticulation poured forth his story.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/5.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: The South she had not thought of seriously; and yet, knowing of its delightful hospitality and mild climate, she was not averse to Charleston or New Orleans..</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/6.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: There Messrs. Johnson and Hammer put into practice many of the ideas now standard in the art, and secured much useful data for the work in New York, of which the story has just been told.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/7.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: Here she would stay, comforted and soothed among the lovely plants and rich exotics, rejoicing the heart of Old Turner the gardener, who since Polly's first rapturous entrance, had taken her into his good graces for all time.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/8.wav"  type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table> -->
<ruby>Text: He examines the horizon all round with his glass, and folds his arms with the air of an injured man.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<!-- <th style="text-align: center">StreamVC</th> -->
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/9.wav" type="audio/wav"></audio></td>
			<!-- <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/9.wav" type="audio/wav"></audio></td> -->
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/9.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<!-- <ruby> Text: In order to please her, I spoke to her of the Abbe Conti, and I had occasion to quote two lines of that profound writer.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Source</th>
			<th style="text-align: center">Conan</th>
			<th style="text-align: center">Conan (fastest)</th>
			<th style="text-align: center">StreamVC</th>
			<th style="text-align: center">QuickVC</th>
			<th style="text-align: center">DiffVC</th>
			<th style="text-align: center">VQMIVC</th>
			<th style="text-align: center">PPGVC</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/Conan_fastest/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/StreamVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/QuickVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/DiffVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/VQMIVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p360/PPGVC/10.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table> -->
