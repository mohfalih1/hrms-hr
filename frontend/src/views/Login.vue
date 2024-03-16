<template>
	<ion-page>
		<ion-content class="ion-padding">
			<div class="flex h-screen w-screen bg-white">
				<div
					class="flex flex-col gap-3 bg-[#A3312A] w-[55%] pl-24 justify-center"
				>
					<!-- <FrappeHRLogo class="h-8 w-8" /> -->
					<div class="flex items-center gap-4">
						<img src="/LogoAlRaya.png" class="w-16" />
						<h2 class="text-white text-3xl font-bold tracking-wider">
							AL'RAIYA GROUP
						</h2>
					</div>

					<h1
						class="text-white text-[54px] font-bold leading-[60px] tracking-wide"
					>
						Welcome To <br />
						Al-Raiya Group
					</h1>
					<p class="text-white font-thin flex items-center">
						Please Login To Use The System
						<FeatherIcon name="chevron-right" class="h-6 w-6" />
						<FeatherIcon name="chevron-right" class="h-6 w-6 -ml-4" />
					</p>
				</div>

				<div
					class="w-[45%] bg-[#FEFBFB] h-full flex justify-center items-center"
				>
					<div>
						<h1 class="font-bold text-3xl text-[#c24c4c] mb-4">Login</h1>
						<form class="flex flex-col gap-4" @submit.prevent="submit">
							<label for="email" class="-mb-3">Email</label>
							<div
								class="bg-white rounded-2xl border border-gray-100/95 h-10 relative overflow-hidden"
							>
								<FeatherIcon
									name="mail"
									class="h-5 w-5 left-1 top-1/2 z-10 -translate-y-[50%] text-[#c24c4c] absolute"
								/>
								<Input
									placeholder="johndoe@mail.com"
									v-model="email"
									id="email"
									class="border-none w-[400px] h-10 m-0 pl-4 bg-white px-0 outline-none focus:shadow-none focus:ring-0 hover:bg-white"
								/>
							</div>

							<!-- :type="email !== 'Administrator' ? 'email' : 'text'" -->
							<label for="password" class="mb-[-10px]">Password</label>
							<div
								class="bg-white rounded-2xl border border-gray-100/95 h-10 relative overflow-hidden"
							>
								<FeatherIcon
									name="lock"
									class="h-5 w-5 left-1 top-1/2 z-10 -translate-y-[50%] text-[#c24c4c] absolute"
								/>
								<Input
									class="border-none w-full h-10 m-0 pl-4 bg-white px-0 outline-none focus:shadow-none focus:ring-0 hover:bg-white"
									type="password"
									id="password"
									placeholder="••••••"
									v-model="password"
									variant="outline"
								/>
							</div>

							<ErrorMessage :message="session.login.error" />
							<Button
								:loading="session.login.loading"
								variant="solid"
								theme="red"
								:disabled="password === null ? true : false"
								class="rounded-2xl text-white bg-[#c24c4c] cursor-pointer"
							>
								<div class="flex justify-between w-full items-center">
									<p class="ml-auto w-full">Login</p>
									<FeatherIcon name="chevron-right" class="h-6 w-6" />
								</div>
							</Button>
						</form>
					</div>
				</div>
			</div>
		</ion-content>
	</ion-page>
</template>

<script setup>
import { IonPage, IonContent } from "@ionic/vue"
import { inject, ref } from "vue"
import { Input, Button, ErrorMessage, FeatherIcon } from "frappe-ui"

import FrappeHRLogo from "@/components/icons/FrappeHRLogo.vue"

const email = ref(null)
const password = ref(null)

const session = inject("$session")
function submit(e) {
	session.login.submit({
		email: email.value,
		password: password.value,
	})
}
</script>
