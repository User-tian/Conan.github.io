

{:.no_toc}
* toc
{:toc}


# Abstract
Zero-shot online voice conversion (VC) holds significant promise for real-time communications and entertainment. However, current VC models struggle to preserve semantic fidelity under real-time constraints, deliver natural-sounding conversions, and adapt effectively to unseen speaker characteristics.
To address these challenges, we introduce Conan, a chunkwise online zero-shot voice conversion model that preserves the content of the source while matching the voice timbre and styles of reference speech. Conan comprises three core components: 1) a Stream Content Extractor that leverages Emformer for low-latency streaming content encoding; 2) an Adaptive Style Encoder that extracts fine-grained stylistic features from reference speech for enhanced style adaptation; 3) a Causal Shuffle Vocoder that implements a fully causal HiFiGAN using a pixel-shuffle mechanism. Experimental evaluations demonstrate that Conan outperforms baseline models in both subjective and objective metrics。


# Samples
During streaming inference, we first feed the entire reference speech into the model to provide timbre and stylistic information. During chunk-wise online inference, we wait until the input reaches a predefined chunk size before passing it to the model. 

We use speech from VCTK as the target speaker, and speech from LibriTTS as the source content.

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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/1.wav" type="audio/wav"></audio></td>

		</tr>
	</tbody>
</table>

<ruby>Text: You see how doubly, how intimately, opposed the ideas are; yet how difficult to explain without apparent contradiction.</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_2.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_3.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/4.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/5.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_6.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_7.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_8.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_9.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/Conan_fastest/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/StreamVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/QuickVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/DiffVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/VQMIVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p231/PPGVC/10.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


## Target Speaker p334
Target Speech: <audio controls style="width: 30%; margin: 15px 0;"><source src="wavs/Origins/p334_001_002_003.wav" type="audio/wav"> </audio>

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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/1.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Text: You see how doubly, how intimately, opposed the ideas are; yet how difficult to explain without apparent contradiction.</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_2.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_3.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_4.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/5.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_5.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_6.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_7.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_8.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_9.wav" type="audio/wav"></audio></td>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/Conan_fastest/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/Origins/Source_Origin_10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/StreamVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/QuickVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/DiffVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/VQMIVC/10.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/p334/PPGVC/10.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
## Target Speaker p362

## Target Speaker p360

## ESD dataset
<ruby>Reference/Target Text: But if you hadn't done them. </ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
            <th style="text-align: center">Reference (voc)</th>
			<th style="text-align: center">Mellotron</th>
			<th style="text-align: center">FG-Transfromer</th>
            <th style="text-align: center">Expressive FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
			<th style="text-align: center">Styler</th>
            <th style="text-align: center">GenerSpeech</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/Reference/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/Reference_voc/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/mellotron/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/FGTransformerTTS/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/FS2/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/StyleSpeech/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/STYLER/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/GenerSpeech/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Reference/Target Text: I say neither yea nor nay.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
            <th style="text-align: center">Reference (voc)</th>
			<th style="text-align: center">Mellotron</th>
			<th style="text-align: center">FG-Transfromer</th>
            <th style="text-align: center">Expressive FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
			<th style="text-align: center">Styler</th>
            <th style="text-align: center">GenerSpeech</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/Reference/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/Reference_voc/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/mellotron/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/FGTransformerTTS/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/FS2/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/StyleSpeech/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/STYLER/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/ESD/GenerSpeech/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>



# Non-Parallel Transfer

In non-parallel style transfer, the TTS system must transfer prosodic style when the source and target text are completely different. Below, contrast the monotonous prosody of the baseline with examples of long-form synthesis with a narrative source style.

## VCTK dataset
<ruby>Reference Text: When the sunlight strikes raindrops in the air, they act as a prism and form a rainbow.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference Audio</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/Reference/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Target Text: We also need a small plastic snake and a big toy frog for the kids.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Mellotron</th>
			<th style="text-align: center">FG-Transfromer</th>
            <th style="text-align: center">Expressive FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
			<th style="text-align: center">Styler</th>
            <th style="text-align: center">GenerSpeech</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/mellotron/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/FGTransformerTTS/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/FS2/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/StyleSpeech/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/STYLER/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/GenerSpeech/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Reference Text: The rainbow is a division of white light into many beautiful colors.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference Audio</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/Reference/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Target Text: Six spoons of fresh snow peas, five thick slabs of blue cheese, and maybe a snack for her brother Bob.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Mellotron</th>
			<th style="text-align: center">FG-Transfromer</th>
            <th style="text-align: center">Expressive FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
			<th style="text-align: center">Styler</th>
            <th style="text-align: center">GenerSpeech</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/mellotron/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/FGTransformerTTS/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/FS2/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/StyleSpeech/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/STYLER/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/VCTK/GenerSpeech/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>



## ESD dataset
<ruby>Reference Text:  I say neither yea nor nay.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference Audio</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/Reference/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Target Text: I know you.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Mellotron</th>
			<th style="text-align: center">FG-Transfromer</th>
            <th style="text-align: center">Expressive FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
			<th style="text-align: center">Styler</th>
            <th style="text-align: center">GenerSpeech</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/mellotron/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/FGTransformerTTS/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/FS2/001.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/StyleSpeech/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/STYLER/001.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/GenerSpeech/001.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Reference Text: All this we have won by our labour.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference Audio</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/Reference/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<ruby>Target Text: Because he was a man with infinite resource and sagacity.</ruby>
<table>
	<thead>
		<tr>
			<th style="text-align: center">Mellotron</th>
			<th style="text-align: center">FG-Transfromer</th>
            <th style="text-align: center">Expressive FastSpeech 2</th>
			<th style="text-align: center">Meta-StyleSpeech</th>
			<th style="text-align: center">Styler</th>
            <th style="text-align: center">GenerSpeech</th>
		</tr>
	</thead>
	<tbody>
		<tr>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/mellotron/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/FGTransformerTTS/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/FS2/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/StyleSpeech/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/STYLER/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/NonParallelTransfer/ESD/GenerSpeech/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

