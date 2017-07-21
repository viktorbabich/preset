<template>
	<div>
		<div class="font">
			<h2>Base font</h2>
			<ul class="font__params">
				<li>
					<span>font-family</span>
					<select v-model="font.baseFont['font-family']">
				    <option disabled>font-family</option>
				    <option>Times New Roman</option>
				    <option>Arial</option>
				    <option>Calibri</option>
				    <option>Georgia</option>
				    <option>Impact</option>
				    <option>Tahoma</option>
				    <option>Verdana</option>
					</select>
				</li>
				<li>
					<span>font-size</span>
					<input type="text" v-model="font.baseFont['font-size']">
				</li>
				<li>
					<span>font-weight</span>
					<input type="text" v-model="font.baseFont['font-weight']"> 
				</li>
				<li>
					<span>line-height</span>
					<input type="text" v-model="font.baseFont['line-height']">
				</li>
				<li>
					<span>letter-spacing</span>
					<input type="text" v-model="font.baseFont['letter-spacing']">
				</li>
			</ul>

		</div>
		<div class="font">
			<h2>Base font</h2>
			<ul class="font__params">
				<li>
					<span>font-family</span>
					<select v-model="font.h1['font-family']">
				    <option disabled>font-family</option>
				    <option>Times New Roman</option>
				    <option>Arial</option>
				    <option>Calibri</option>
				    <option>Georgia</option>
				    <option>Impact</option>
				    <option>Tahoma</option>
				    <option>Verdana</option>
					</select>
				</li>
				<li>
					<span>font-size</span>
					<input type="text" v-model="font.h1['font-size']">
				</li>
				<li>
					<span>font-weight</span>
					<input type="text" v-model="font.h1['font-weight']"> 
				</li>
				<li>
					<span>line-height</span>
					<input type="text" v-model="font.h1['line-height']">
				</li>
				<li>
					<span>letter-spacing</span>
					<input type="text" v-model="font.h1['letter-spacing']">
				</li>
			</ul>
			<div class="preview">
				<div class="base-font" :style="{
					'font-family': font.baseFont['font-family'],
					fontSize: font.baseFont['font-size']  + 'px',
					'font-weight': font.baseFont.fw,
					'line-height': font.baseFont.lh + 'em',
					'letter-spacing': font.baseFont.ls + 'em',
				}">Lorem ipsum dolor sit amet, consectetur adipisicing elit.
				</div>
				<div class="h1" :style="{
					'font-family': font.h1['font-family'],
					fontSize: font.h1['font-size']  + 'px',
					'font-weight': font.h1['font-weight'],
					'line-height': font.h1['line-height'] + 'em',
					'letter-spacing': font.h1['letter-spacing'] + 'em',
				}">Lorem ipsum dolor sit amet, consectetur adipisicing elit.
				</div>
			</div>
		</div>
		<a href="" @click.prevent="printLessConfig">Save data</a>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				font: {
					baseFont: {
						"font-family": "Arial",
						"font-size": 16,
						"font-weight": 400,
						"line-height": 1.2,
						"letter-spacing": 0
					},
					h1: {
						"font-family": "Arial",
						"font-size": 16,
						"font-weight": 400,
						"line-height": 1.2,
						"letter-spacing": 0
					}
				}
			}
		}, 
		methods: {
			generateLessPart (obj, objName) {
			  let str = '';
			  if(objName == "baseFont") {
			  	for(var key in obj) {
			    	str += `@base-${key}: ${obj[key]}\n`
			    };
			  } else {
		  		for(var key in obj) {
			    	str += `${key}: ${obj[key]}\n`
		  	  };
		  	  str = `${objName} {\n${str}}`
			  } 
			  return str
			},
			printLessConfig () {
				let result = "";
		   	for (var obj in this.font) {
		    	result += this.generateLessPart(this.font[obj], obj);
		    	result += `\n`
		  	};
			  console.log(result)
			}
		}
	}

</script>

<style lang="scss"> 
	.font {
		&__params {
			list-style-type: none;
			border: 1px solid black;
			padding: 10px;
			width: 190px;
			li {
				margin-bottom: .5em;
				&:last-child {
					margin-bottom: 0;
				}
			}
			select {
				width: 50px;
				display: inline-block;
			}
			span {
				display: inline-block;
				width: 120px;
				margin-right: -0.25em;
			}
			input {
				width: 50px;
				text-align: center;
				margin-right: -0.25em;
			}
		}
	}
</style>


