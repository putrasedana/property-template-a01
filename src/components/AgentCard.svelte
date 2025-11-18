<script lang="ts">
  import { Phone, Mail, Briefcase, Clock } from "lucide-svelte";
  export let agent;
</script>

<div
  class="bg-white rounded-xl shadow-md overflow-hidden hover:shadow-xl transition-shadow duration-300"
>
  <div class="relative overflow-hidden h-64">
    <img
      src={agent.image}
      alt={agent.name}
      class="w-full h-full object-cover"
    />
  </div>

  <div class="p-6">
    <h3 class="text-xl font-bold text-gray-900 mb-1">{agent.name}</h3>
    <p class="text-primary-600 font-medium mb-3">{agent.title}</p>

    <div class="space-y-2 mb-4">
      <div class="flex items-center gap-2 text-sm text-gray-600">
        <Briefcase class="w-4 h-4 text-primary-600" />
        <span>{agent.specialization}</span>
      </div>
      <div class="flex items-center gap-2 text-sm text-gray-600">
        <Clock class="w-4 h-4 text-primary-600" />
        <span>{agent.experience} experience</span>
      </div>
    </div>

    <p class="text-sm text-gray-600 mb-4 line-clamp-3">{agent.bio}</p>

    <div class="space-y-3 border-t border-gray-200 pt-4">
      <a
        href={`tel:${agent.phone}`}
        class="w-full flex items-center justify-center gap-2 bg-gray-100 text-gray-700 px-4 py-3 rounded-lg hover:bg-gray-200 transition-colors font-medium text-sm"
      >
        <Phone class="w-4 h-4" />
        Call Now
      </a>

      <a
        href={`mailto:${agent.email}`}
        class="w-full flex items-center justify-center gap-2 bg-gray-100 text-gray-700 px-4 py-3 rounded-lg hover:bg-gray-200 transition-colors font-medium text-sm"
      >
        <Mail class="w-4 h-4" />
        Send Email
      </a>
    </div>
  </div>
</div>
