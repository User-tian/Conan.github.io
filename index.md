

{:.no_toc}
* toc
{:toc}


# Abstract
Style transfer for out-of-domain (OOD) speech synthesis aims to generate speech samples with unseen style (e.g., speaker identity, emotion, and prosody) derived from an acoustic reference, while facing the following challenges: 1) The highly dynamic style features in expressive voice are difficult to model and transfer; and 2) the TTS models should be robust enough to handle diverse OOD conditions that differ from the source data. This paper proposes GenerSpeech, a text-to-speech model towards high-fidelity zero-shot style transfer of OOD custom voice. GenerSpeech decomposes the speech variation into the style-agnostic and style-specific parts by introducing two components: 1) a multi-level style adaptor to efficiently model a large range of style conditions, including global speaker and emotion characteristics, and the local (utterance, phoneme, and word-level) fine-grained prosodic representations; and 2) a generalizable content adaptor with Mix-Style Layer Normalization to eliminate style information in the linguistic content representation and thus improve model generalization. Our evaluations on zero-shot style transfer demonstrate that GenerSpeech surpasses the state-of-the-art models in terms of audio quality and style similarity. The extension studies to adaptive style transfer further show that GenerSpeech performs robustly in the few-shot data setting.

# Parallel Style Transfer

 In parallel style transfer, the synthesizer is given an audio clip matching the text it's asked to synthesize (i.e. the reference and target text are the same).

## VCTK dataset
<ruby>Reference/Target Text: The rainbow is a division of white light into many beautiful colors.</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/GT/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/GT_voc/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/mellotron/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/FGTransformerTTS/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/FS2/003.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/StyleSpeech/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/STYLER/003.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/GenerSpeech/003.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<ruby>Reference/Target Text: When the sunlight strikes raindrops in the air, they act as a prism and form a rainbow.</ruby>
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
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/GT/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/GT_voc/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/mellotron/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/FGTransformerTTS/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/FS2/002.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/StyleSpeech/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/STYLER/002.wav" type="audio/wav"></audio></td>
            <td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ParallelTransfer/VCTK/GenerSpeech/002.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


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

