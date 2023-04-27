# CraftbleNameTags
Just Craftble Name Tags


Source code:

package me.vlasov.craftblenametags;

import org.bukkit.Bukkit;
import org.bukkit.ChatColor;
import org.bukkit.Material;
import org.bukkit.NamespacedKey;
import org.bukkit.block.data.type.Light;
import org.bukkit.enchantments.Enchantment;
import org.bukkit.inventory.ItemFlag;
import org.bukkit.inventory.ItemStack;
import org.bukkit.inventory.ShapedRecipe;
import org.bukkit.inventory.meta.ItemMeta;
import org.bukkit.inventory.meta.PotionMeta;
import org.bukkit.plugin.java.JavaPlugin;

import java.util.logging.Level;

public final class CraftbleNameTags extends JavaPlugin {

    @Override
    public void onEnable() {
        // Our custom variable which we will be changing around.
        ItemStack item = new ItemStack(Material.NAME_TAG);


        // The meta of the diamond sword where we can change the name, and properties of the item.
        ItemMeta meta = item.getItemMeta();


        // We will initialise the next variable after changing the properties of the sword


        // This sets the name of the item.
        //meta.setDisplayName(ChatColor.WHITE + "Name Tag");
        //carrotmeta.setDisplayName(ChatColor.WHITE + "Golden Carrot");

        // Set the meta of the sword to the edited meta.
        item.setItemMeta(meta);

        // Add the custom enchantment to make the emerald sword special
        // In this case, we're adding the permission that modifies the damage value on level 5
        // Level 5 is represented by the second parameter. You can change this to anything compatible with a sword
        //item.addEnchantment(Enchantment.DAMAGE_ALL, 5);




        // create a NamespacedKey for your recipe
        NamespacedKey key = new NamespacedKey(this, "name_tag");

        // Create our custom recipe variable
        ShapedRecipe recipe = new ShapedRecipe(key, item);

        item:

        // Here we will set the places. P, S and I can represent anything, and the letters can be anything.
        recipe.shape(" SS", "PIP", "PPP");



        // Set what the letters represent.
        // P = Paper, S = String, I = Glow ink sac
        recipe.setIngredient('P', Material.PAPER);
        recipe.setIngredient('S', Material.STRING);
        recipe.setIngredient('I', Material.GLOW_INK_SAC);


        // Finally, add the recipe to the bukkit recipes
        Bukkit.addRecipe(recipe);

    }

    @Override
    public void onDisable() {
        // Plugin shutdown logic
    }
}
