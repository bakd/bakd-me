<template>
	<router-link :to="{ name: 'members.dashboard' }">
		<div class="widget">
			<!-- MY ACCOUNT WIDGET -->
			<p class="has-text-left title is-size-5">
				My Account
			</p>
			<div class="box has-text-centered">
				
				<article class="media">
					<div class="media-left is-64x64">
						<img :src="user.photo_url" class="is-v-centered image is-64x64" style="height: auto; width: 100%; max-width: 64px" />
					</div>
					<div class="media-content">
						<div class="user-info">
							<span class="title is-size-6 has-text-left is-marginless">
								{{ user.name }} 
							</span>
							<!-- <span class="is-bold">Trust:</span>  -->
							<b-tooltip label="Trust Level" type="is-dark">
								<span class="is-bold is-green is-size-7">+10,200</span>
							</b-tooltip>
						<!-- </div> -->
							<p class="subtitle is-size-7 has-text-gray-light is-marginless">
								Blockchain Developer
							</p>
							<p class="user-trust is-size-7" style="padding-top: 3px;">
								<span class="tag is-green is-small is-size-7" style="height: unset; padding-top: .1rem; padding-bottom: .1rem;"><fa icon="star"/>&nbsp;&nbsp;VERIFIED</span>
							</p>
						</div>
					</div>
				</article>
			</div>
		</div>
	</router-link>
</template>

<script>
import { mapGetters } from "vuex"

export default {

  computed: mapGetters({
    user: 'auth/user'
  }),

}
</script>