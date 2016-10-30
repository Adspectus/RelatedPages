Kirby-RelatedPages
==================

## RelatedPages Plugin for Kirby CMS

The RelatedPages plugin provides an easy, but flexible way of incorporating links (or other data) of related pages to the current page. The relationsship is considered by keywords in an arbitrary field of the content files. Example: If you provide the field 'Tags' in your content file which is rendered together with the RelatedPages plugin, all pages in your site will be searched for any of the *tags* (separated by comma) in the field 'Tags'. The plugin returns a page collection object with all related pages.

### Installation

Save the file `relatedpages.php` into the relatedpages subfolder of the plugins folder of Kirby 2.

### Basic usage

```php
<?php $relpages = relatedpages(); ?>
```
#### Example

```html
<ul>
  <?php foreach(relatedpages() as $relpage): ?>
    <li><a href="<?php echo $relpage->url() ?>"><?php echo $relpage->title() ?></a></li>
  <?php endforeach ?>
</ul>
```
 
### Options

You can control which pages are searched for and which pages are found by a number of options, which should be supplied as an associative array:

```php
<?php $MyRelatedPages = relatedpages($Options); ?>
```

#### Example

```php
$Options = array('visibleOnly' => false, 'recursionDepth' => 1);
```

This will find all pages, not only visible pages, and the depth of recursion is 1, which means 1 level down the page hierachy starting at the root level.

#### Possible options

| Key            | Value   | Default | Description |
|----------------|---------|---------|-------------|
| visibleOnly    | Bool    | true    | If true, searches only visible pages, otherwise all. |
| startURI       | String  | ''      | Start folder of search. If blank, starts at the root level. Use only folder names without numbers. No trailing slash. Example: '/folder/subfolder' |
| recursionDepth | Integer | 0       | Depth of recursion into the folder structure. 0 means infinitely. Count starts at StartURI level, this means it is relative to the root level. |
| searchField    | String  | 'Tags'  | The name of the field in your content file which holds the keywords. |
| searchItems    | Array   | array() | A list of keywords which should be searched for. An empty array means that all keywords which are found in the 'searchField' will be searched for. |
| minHits        | Integer | 1       | Number of minimum required hits of searchItems.

For backward compatibility, you can still use the old option names:

'VisibleOnly'

'StartURI'

'Depth'

'Field'

'Items'
 
