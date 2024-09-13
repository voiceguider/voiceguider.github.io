## VoiceGuider: Enhancing Out-of-Domain Performance in Parameter-Efficient Speaker-Adaptive Text-to-Speech via Autoguidance (Submitted to ICASSP 2025)

### Authors
- Jiheum Yeom <a href="quilava1234@snu.ac.kr">quilava1234@snu.ac.kr</a>
- Heeseung Kim <a href="gmltmd789@snu.ac.kr">gmltmd789@snu.ac.kr</a>
- Jooyoung Choi <a href="jy_choi@snu.ac.kr">jy_choi@snu.ac.kr</a>
- Che Hyun Lee <a href="saga1214@snu.ac.kr">saga1214@snu.ac.kr</a>
- Nohil Park <a href="pnoil2588@snu.ac.kr">pnoil2588@snu.ac.kr</a>
- Sungroh Yoon (Corresponding author) <a href="sryoon@snu.ac.kr">sryoon@snu.ac.kr</a>

## Abstract

When applying parameter-efficient finetuning via LoRA onto speaker adaptive text-to-speech models, adaptation performance may decline compared to full-finetuned counterparts, especially for out-of-domain speakers. Here, we propose VoiceGuider, a parameter-efficient speaker adaptive text-to-speech system reinforced with autoguidance to enhance the speaker adaptation performance, reducing the gap against full-finetuned models. We carefully explore various ways of strengthening autoguidance, ultimately finding the optimal strategy. VoiceGuider as a result shows robust adaptation performance especially on extreme out-of-domain speech data. We provide audible samples in our demo page.



<b> All generated voices where resampled to 16kHz and normalized to -27dB for fair comparison. </b>


## Comparison between Full-finetuning (UnitSpeech) and LoRA-tuning (VoiceTailor) on Different Domains of Datasets

### <b>LibriTTS</b>: In-domain dataset used for pretraining. Reference speakers are randomly chosen from the test set.

Transcript: But Polly couldn't speak and if Jasper hadn't caught her just in time, she would have tumbled over backward from the stool, Phronsie and all!
<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">GT</th>
			<th style="text-align: center">UnitSpeech</th>
			<th style="text-align: center">VoiceTailor</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/libritts/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/libritts/ground truth.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/libritts/unitspeech.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/libritts/voicetailor.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

### <b>VCTK</b>: Out-of-domain dataset not used for pretraining.

Transcript: We decided we would go for a specialist inside centre.
<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">GT</th>
			<th style="text-align: center">UnitSpeech</th>
			<th style="text-align: center">VoiceTailor</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/vctk/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/vctk/ground truth.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/vctk/unitspeech.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/vctk/voicetailor.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

### <b>GigaSpeech</b>: A more extreme case of out-of-domain dataset. Often contains data collect from in-the-wild situations such as youtube.

Transcript: Tired of eating the same old food, fancy a taste of some of the finest ingredients money can buy.
<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">GT</th>
			<th style="text-align: center">UnitSpeech</th>
			<th style="text-align: center">VoiceTailor</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/gigaspeech/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/gigaspeech/ground truth.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/gigaspeech/unitspeech.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/problem_statement/gigaspeech/voicetailor.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

<br><br><br>

## Adaptive Text-to-Speech Model Comparison on GigaSpeech

Transcript: That was of course until the steam powered loom came into the picture. With weaving technology rapidly improving, his father's loom business would crumble finding himself crushed by the industrial revolution.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">GT</th>
			<th style="text-align: center">XTTS v2</th>
			<th style="text-align: center">CosyVoice</th>
			<th style="text-align: center">UnitSpeech</th>
			<th style="text-align: center">VoiceTailor</th>
			<th style="text-align: center"><b>VoiceGuider</b></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/1/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/1/ground truth.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/1/xttsv2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/1/cosyvoice.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/1/unitspeech.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/1/voicetailor.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/1/voiceguider.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


Transcript: This video would not have been possible if it wasn't for our friends at acorns and investment app with over six million users that makes investing as easy as spending.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">GT</th>
			<th style="text-align: center">XTTS v2</th>
			<th style="text-align: center">CosyVoice</th>
			<th style="text-align: center">UnitSpeech</th>
			<th style="text-align: center">VoiceTailor</th>
			<th style="text-align: center"><b>VoiceGuider</b></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/2/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/2/ground truth.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/2/xttsv2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/2/cosyvoice.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/2/unitspeech.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/2/voicetailor.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/2/voiceguider.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Transcript: And your heart skips a beat, and you're like a dead for a millisecond or something. um, yeah, clearly not true.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">GT</th>
			<th style="text-align: center">XTTS v2</th>
			<th style="text-align: center">CosyVoice</th>
			<th style="text-align: center">UnitSpeech</th>
			<th style="text-align: center">VoiceTailor</th>
			<th style="text-align: center"><b>VoiceGuider</b></th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/3/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/3/ground truth.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/3/xttsv2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/3/cosyvoice.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/3/unitspeech.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/3/voicetailor.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/comparison/3/voiceguider.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


<br><br><br>

## Ablation Studies


### Number of training iterations for the Inferior Model used for Autoguidance

Transcript: But if you want to shell out and see for yourself, you'll have to head down to australia is at peninsula.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">Iteration 0</th>
			<th style="text-align: center">Iteration 100 <strong>(default)</strong></th>
			<th style="text-align: center">Iteration 200</th>
			<th style="text-align: center">Iteration 300</th>
			<th style="text-align: center">Iteration 400</th>
			<th style="text-align: center">Iteration 500</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/1/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/1/0.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/1/100.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/1/200.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/1/300.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/1/400.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/1/500.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


Transcript: Caffeine has been shown to boost metabolism by up to eleven percent and dramatically increase fat burning potential.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">Iteration 0</th>
			<th style="text-align: center">Iteration 100 <strong>(default)</strong></th>
			<th style="text-align: center">Iteration 200</th>
			<th style="text-align: center">Iteration 300</th>
			<th style="text-align: center">Iteration 400</th>
			<th style="text-align: center">Iteration 500</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/2/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/2/0.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/2/100.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/2/200.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/2/300.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/2/400.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_iteration/2/500.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<br>

### Rank $r$ for Autoguidance Model

Transcript: Giving is most fulfilling when you donate your money or time to a cause you're passionate about.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">$r = 1$ <strong>(default)</strong></th>
			<th style="text-align: center">$r = 2$</th>
			<th style="text-align: center">$r = 4$</th>
			<th style="text-align: center">$r = 8$</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/1/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/1/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/1/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/1/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/1/8.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Transcript: In order to boost public interest in space exploration and hopefully increase nasa's budget.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">$r = 1$ <strong>(default)</strong></th>
			<th style="text-align: center">$r = 2$</th>
			<th style="text-align: center">$r = 4$</th>
			<th style="text-align: center">$r = 8$</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/2/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/2/1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/2/2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/2/4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_rank/2/8.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<br>

### Autoguidance Scale $\gamma_a$

Transcript: And brought them both to multi billion dollar valuations.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">$\gamma_a = 0.0$</th>
			<th style="text-align: center">$\gamma_a = 0.33$</th>
			<th style="text-align: center">$\gamma_a = 0.66$</th>
			<th style="text-align: center">$\gamma_a = 1.0$ <strong>(default)</strong></th>
			<th style="text-align: center">$\gamma_a = 1.33$</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/1/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/1/0.0.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/1/0.33.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/1/0.66.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/1/1.0.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/1/1.33.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>


Transcript: Waiting for carbs mistakes and the game was adjourned to be resumed next day.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">$\gamma_a = 0.0$</th>
			<th style="text-align: center">$\gamma_a = 0.33$</th>
			<th style="text-align: center">$\gamma_a = 0.66$</th>
			<th style="text-align: center">$\gamma_a = 1.0$<strong>(default)</strong></th>
			<th style="text-align: center">$\gamma_a = 1.33$</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/2/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/2/0.0.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/2/0.33.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/2/0.66.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/2/1.0.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_scale/2/1.33.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<br>

### Upper Guidance Interval $t_{hi}$ 

Transcript: Always do a proper analysis but regardless these rules of thumb can come in really handy in saving you from analyzing every single deal that you've come across.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">$t_{hi} = 0.9$</th>
			<th style="text-align: center">$t_{hi} = 0.8$</th>
			<th style="text-align: center">$t_{hi} = 0.7$</th>
			<th style="text-align: center">$t_{hi} = 0.6$ <strong>(default)</strong></th>
			<th style="text-align: center">$t_{hi} = 0.5$</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/1/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/1/0.9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/1/0.8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/1/0.7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/1/0.6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/1/0.5.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Transcript: And the nine scientific benefits to having a daily cup of joe.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">$t_{hi} = 0.9$</th>
			<th style="text-align: center">$t_{hi} = 0.8$</th>
			<th style="text-align: center">$t_{hi} = 0.7$</th>
			<th style="text-align: center">$t_{hi} = 0.6$ <strong>(default)</strong></th>
			<th style="text-align: center">$t_{hi} = 0.5$</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/2/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/2/0.9.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/2/0.8.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/2/0.7.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/2/0.6.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_upper/2/0.5.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>
<br>

### Lower Guidance Interval $t_{lo}$

Transcript: So i'll just get right into it. The first is an easy one that's actually in my artist of life workbook, is to list ten things that you love about yourself

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">$t_{lo} = 0.1$ <strong>(default)</strong></th>
			<th style="text-align: center">$t_{lo} = 0.2$</th>
			<th style="text-align: center">$t_{lo} = 0.3$</th>
			<th style="text-align: center">$t_{lo} = 0.4$</th>
			<th style="text-align: center">$t_{lo} = 0.5$</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/1/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/1/0.1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/1/0.2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/1/0.3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/1/0.4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/1/0.5.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

Transcript: It can also help to commit to a consistent donation over time and to focus on the less glamorous but essential needs the charity may have.

<table>
	<thead>
		<tr>
			<th style="text-align: center">Reference</th>
			<th style="text-align: center">$t_{lo} = 0.1$ <strong>(default)</strong></th>
			<th style="text-align: center">$t_{lo} = 0.2$</th>
			<th style="text-align: center">$t_{lo} = 0.3$</th>
			<th style="text-align: center">$t_{lo} = 0.4$</th>
			<th style="text-align: center">$t_{lo} = 0.5$</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/2/reference.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/2/0.1.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/2/0.2.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/2/0.3.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/2/0.4.wav" type="audio/wav"></audio></td>
			<td style="text-align: center"><audio controls style="width: 150px;"><source src="wavs/ablation_lower/2/0.5.wav" type="audio/wav"></audio></td>
		</tr>
	</tbody>
</table>

